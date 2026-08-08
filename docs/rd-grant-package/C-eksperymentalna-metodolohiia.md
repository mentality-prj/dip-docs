# C. Experimental Methodology

> R&D Grant Package
> Version: 0.1 | 2026-08-08 | Draft

## Meta

Визначити повний протокол перевірки гіпотез H1–H5 так, щоб кожен аспект міг бути незалежно відтворений.

---

## 1. Datasets

### 1.1 Syntetychni dani (priorittet dlya B+R fazy)

Prychyna: etychni obmezhennya na real'ni dani na rannikh etapakh, neobkhidnist' kontrol'ovanykh umov.

**Metod generatsiyi:**

- CTGAN (Conditional Tabular GAN) abo Gaussian Copula dlya vidtvorennya realʼnykh rozpodiliv
- Time-series synthetic: AR(1) model dlya bazovykh tendentsiy + shumuvi addytyvni
- Kontorol: heneruyuty dani z vidomymy vlastyvostyamy (CE pidtselyuyemo na 0.10, 0.20, 0.30) dlya kalibruvalnykh tektiv

**Kharakterystyky sintetychnoho naboru:**

- N = 500–1000 syntetychnykh korystuvachiv
- T = 90 dniv zapysiv (dailya)
- Rozpodil ryzykovykh podiy: ~15–20% "worsened" outcomes
- Rozkydy parametriv: alpha ∈ [0.1, 0.6], baseline variance ∈ [0.15, 0.8]

### 1.2 Realni anoniimizovani dani

Dostupni pislya etychnoho poghodzhennya ta pidpysannya DMP.

- Pseudoniimizovani zapysy mood/stress/energy/focus z Dzvin.co
- Minkohort: ≥ k-anonimnist' 5 (prysrednuvannya pered eksportom)
- Tilky agrehovani na komandnomu rivni dlya komandnykh eksperymentiv

---

## 2. Train / Validation / Test Split

**Pravylo:** time-based split — neyakyi vitik z maibutniokh danykh v trenuvannya.

```
Usi dani: [--- Train (60%) ---][-- Val (20%) --][- Test (20%) -]
           t=0           t_cut1           t_cut2           t_end
```

- Train: optyalizatsiya vahiv (Д4), navchannya baseline (Д8)
- Validation: vibir gipeprametryv (alpha, rho, margin delta)
- Test: odnorazova ocinka — ne torkatysya do finalnykh rezul'tativ

**Rolling-origin backtest:**

- Zysuvatyy t_cut1 na tyzden' za raz (5–10 raziv)
- Metry'ky zvituyut' mid ± CI po vsikh persereshchuvanyakh

---

## 3. Baseline Models

| #   | Nazva                   | Opys                                             | Kompleksnist'          |
| --- | ----------------------- | ------------------------------------------------ | ---------------------- |
| B1  | Rule threshold          | stress ≥ 4.0 → high; < 4.0 → low                 | Minimal                |
| B2  | Population z-score      | (s - mean_pop) / std_pop ≥ 1.5 → high            | Minimal                |
| B3  | EWMA manual             | Potochnyy riskScore z manual w=(0.34,...)        | Pootoochnyy production |
| B4  | Logistic regression     | Trained na {s_t, s_7d, s_14d, delta_s, vol, m_t} | ML classic             |
| B5  | Simple EWMA (no vector) | EWMA stress only, no multi-dim state             | Ablatsiya              |
| B6  | Proposed model          | Optimized w + bootstrap CI + minimax             | Zaproponuvanyy         |

---

## 4. Metrics

### 4.1 Primary metrics (hypothesis tests)

| Metryka                | Formyla                          | Gipoteza | Porivnyannya                       |
| ---------------------- | -------------------------------- | -------- | ---------------------------------- |
| Calibration Error (CE) | $(1/N)\sum\|p_i - y_i\|$         | H1, H4   | Paired t-test: CE(B6) vs CE(B3/B2) |
| AUROC                  | Area under ROC                   | H2       | DeLong test: AUC(B6) vs AUC(B1/B3) |
| Minimax coverage       | $P(Y \in [R_{best}, R_{worst}])$ | H3       | Coverage test vs 90% target        |
| Brier Score            | $(1/N)\sum(p_i - y_i)^2$         | H4       | Paired t-test                      |
| r(stability, drift)    | Pearson correlation              | H5       | t-test: r ≠ 0                      |

### 4.2 Secondary metrics

- Precision@high-risk: tochnis' sered top-10% za perebaychenoiu ryzyku
- False Positive Rate (FPR): chastka khybno pozyrvnyatykh prognoziv
- False Negative Rate (FNR): chastka propushchenykh vysokory'zkovykh podyii
- Policy stability index: chastota zminy rishennya pry malomu zmini vkhidnykh danykh

---

## 5. Statistical Tests

### 5.1 Hypothesis tests

| Gipoteza                          | Test                       | Umova fal'syfikatsiyi              |
| --------------------------------- | -------------------------- | ---------------------------------- | --- | ------------------ |
| H1: CE(EWMA) < CE(population)     | Paired t-test abo Wilcoxon | p ≥ 0.05 ABO CI mist' 0            |
| H2: AUROC(vector) > AUROC(scalar) | DeLong test                | p ≥ 0.05 ABO delta_AUC < 0.02      |
| H3: coverage ≥ 90%                | Binomial test              | Konfidensiynyy interval nyzche 90% |
| H4: CE(opt_w) < CE(manual_w)      | Paired t-test              | p ≥ 0.05                           |
| H5: r ≠ 0                         | Pearson t-test             |                                    | r   | < 0.3 ABO p ≥ 0.05 |

### 5.2 Multiple comparison correction

Pry odnochasnomu testuvanni H1–H5: zastosuvatyy Benjamini-Hochberg (FDR 5%) dlya otrymannya adzhustovannykh p-values.

### 5.3 Effect size reporting

Dlya kozhnoi gipotezy zvituvaty:

- Kohen'd abo eta^2 (pryrodni syla efektu)
- 95% CI dlya deL'ta metryki
- Practical significance threshold (minimal important difference)

---

## 6. Backtesting Protocol

```
For t_split in [t_30, t_37, t_44, t_51, t_58]:
    Train model on data[:t_split]
    Evaluate on data[t_split : t_split+7]
    Record metrics: AUROC, CE, coverage, FPR
Report: mean ± std for each metric across splits
```

---

## 7. Uncertainty and Robustness Checks

### 7.1 Sensitivity analysis

Zmina odnoho parametra pry fiksovanykh inshykh:

- alpha ∈ {0.1, 0.2, 0.3, 0.38, 0.5} → delta CE
- rho ∈ {0.80, 0.85, 0.92, 0.95} → delta CE
- Margins delta_d ×{0.5, 1.0, 1.5, 2.0} → delta coverage

### 7.2 Out-of-distribution test

Trenuvannya na kokhortakh typu A, testuvannya na kokhortakh typu B:

- Company size shift (malyi → velykyi)
- Engagement shift (vysoke → nyzke)
- Temporal shift (trymaist' → nyzhche)

### 7.3 Drift simulation

Progresyvno vnosyty znachushche znachennya stress_t v testovi dani:

- Stresschnyi test: chi utozhnyuye model' stsenariyi riziku yak "stable"?
- Perevirka systemnoyi stabilnosti (H5)

---

## 8. Reproducibility Requirements

- Vsi eksperymenty loguiutyy experiment manifest (dataset version, code version, random_seed, config)
- Vmist' faylu `experiment-manifest.yaml` fiksuyetsya pered zapuskom
- Random seeds fiksovani (42, 123, 999) — zvitovuyutyy variance mizi seedamy
- Kod u doslidnytskomu repozytoriyi, tehy priv'yazani do rezultativ

---

## Posylannya

- Pov'yazani dokumenty: A-naukova-postanovka.md (H1-H5), B-plan-br.md (Д7, Д8, Д10)
- Formuly: ../grant/appendices/A03-metrics-calculation-sheet.md
- PARP Ścieżka SMART: https://www.parp.gov.pl/harmonogram-naborow/grants/sciezka-smart
- EIC Pathfinder: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
