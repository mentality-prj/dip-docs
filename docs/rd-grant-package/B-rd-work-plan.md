# B. Plan B+R — Etapy Д1–Д10

> Ścieżka SMART B+R — Dokumenty B
> Versiya: 0.1 | 2026-08-08 | Chernetchka

## Logika struktury

B+R-proekt maye perekhodyty vid teoriyi do eksperymentu liniino:

```
Formalizatsiya → Modeli → Alhorytm → Eksperyment → Prototip → Validatsiya
```

U strukturi SMART 2026 modul'nist' prybrali: B+R ye oboviazkovoyu skladovoyu proektu, a kozhne zavdannya (Д) vidpovidaye odnomu doslidnomu etapu.

---

## Д1 — Formalizatsiya modeli

**Meta:** Pereklasty pryktychnu realizatsiyu `adaptive-risk.engine` na formaL'nu matematychnu movu, придатnu dlya naukovoi publikatsiyi ta dovodu.

**Vkhidni dani:**

- Diyuchyy kod `adaptive-risk.engine.ts`
- Formuly z A03-metrics-calculation-sheet.md
- Naukova literatura: EWMA, state-space models, robust estimation

**Metod:**

- Formalne vyznachennya vsikh zminnych ta operatoriv
- Postanovka zadachi optymizatsiyi $\hat{\mathbf{w}}$
- Analiz umov isnuvannya optymalnykh znachen parametriv
- Uzgodzhennya z akademichnym partnerom (KNU)

**Rezultat:**

- Formalna spetsyfikatsiya modeli (LaTeX)
- Tezy dlya naukivtsya z KNU

**Kryterii uspikhu:**

- Model' formalizovana tak, shcho z neyi mozhna vyvesty pereviruvani teoremy
- Aktseptovana akademichnym partnerom

**Riven' hotovnosti:** TRL 2 → TRL 3

---

## Д2 — Model' dynamiky stanu

**Meta:** Pobuduvaty formalu model' togo, yak vektor stanu $\mathbf{x}_t$ zminyuyetsya v chasi.

**Vkhidni dani:**

- Rivnyannya perekhodu z `adaptive-risk.engine.ts`:
  ```
  stress_{t+1} = clamp(s_t + trend×0.55 + vol×0.35 - r×0.45 + (1-ζ)×0.20)
  mood_{t+1}   = clamp(m_t + trend×0.55 + r×0.35 - vol×0.25 - (1-ζ)×0.15)
  ```
- Literaturni stokhastychi modeli: AR(p), state-space (Kalman), HMM

**Metod:**

- Porivnyannya determinovanoho modelu perehodu z stokhastychnym
- Ocinka: chy dostatno EWMA dlya modelyuvannya, chy potrebuye stochastychnoho shlayeru
- Teoretychna analiz stabilnosti sysEmy (Lyapunov / spectral analysis)

**Rezultat:**

- Formalna model' perekhodu $\mathbf{x}_{t+1} = F(\mathbf{x}_t, \boldsymbol{\epsilon}_t)$
- Analiz stabilnosti modeli

**Kryterii uspikhu:**

- Identyfichovano, chy ye model' markovivs'koyu / chystodoterministychnoyu / zvisnoyu
- Opys umov stabilnosti

**Riven' hotovnosti:** TRL 2 → TRL 3

---

## Д3 — Model' nevyznachenosti ta dovirichy intervaly

**Meta:** Zaminyty konservatyvni marzheni $\Delta_d$ empirichnymy dovirichy intervalamy.

**Vkhidni dani:**

- Pobudovani marzheni z kodu:
  ```
  Δ_stress = max((CI_upper - CI_lower)/2, 0.18)
  ```
- Bootstrap CI teoriya (Efron & Tibshirani)
- Peryodni realni dani (abo syntetychni, yakshcho realni ne dostupni)

**Metod:**

- Bootstrap CI z stratyfikatsiyeyu po kokhortakh
- Porivnyannya: chynni konservatyvni vs bootstrap vs bayesivski CI
- Ocinka pokryttya (coverage test): $P(Y_{\text{actual}} \in [R_{\text{best}}, R_{\text{worst}}])$

**Rezultat:**

- Metod rozrakhunku $\Delta_d$ zi statystychnym obgruntuvannyam
- Tablitsya pokryttya za kokhortamy

**Kryterii uspikhu:**

- Coverage rate ≥ 90% na held-out vybirtsi
- CI vuzhe za konservatyvnymy (vyvishennya informatyvnosti)

**Riven' hotovnosti:** TRL 3 → TRL 4

---

## Д4 — Optymizatsiya vahiv (state risk weights)

**Meta:** Zaminyty ruchno zadani vahy $\mathbf{w} = (0.34, 0.22, \ldots)$ na vyznacheni cherez rozv'yazannya zadachi optymizatsiyi.

**Vkhidni dani:**

- Labeled outcome data: pary $(\mathbf{x}_t, Y_{\text{actual}})$, de $Y \in \{0, 1\}$
- Vymogha: $\sum w_i = 1$, $w_i \geq 0$

**Metod:**

- Constrained optimization: projected gradient / SLSQP
- Kros-validatsiya: time-based split (train < cutoff, test ≥ cutoff)
- Porivnyannya CE(manual) vs CE(optimized) na test-vybirtsi

**Formalna zadacha:**
$$\hat{\mathbf{w}} = \arg\min_{\mathbf{w}} \frac{1}{N}\sum_i |\text{riskScore}_i(\mathbf{w}) - Y_i| \quad \text{s.t.}\quad \sum w_j = 1,\; w_j \geq 0$$

**Rezultat:**

- Optymalni vahy $\hat{\mathbf{w}}$ z CI
- Tablitsya: calibration error manual vs optimized

**Kryterii uspikhu:**

- Stattystychno znachushche znyzhennya CE (paired t-test, p < 0.05)
- Stabilnist vahy na 5-fold cross-validation (CV variance < 0.05)

**Riven' hotovnosti:** TRL 3 → TRL 5

---

## Д5 — Model' poshyrennya ryzyku na komandnyy riven'

**Meta:** Formalizuvaty, yak indyvidual'ni ryzyky obiednuyutsya v komandnyy ryzykovyy syhnal.

**Vkhidni dani:**

- Burnout Index formula (A03-metrics-calculation-sheet.md)
- Team coupling bonus: `synergy = (1 - teamSyncDeviation) × 0.25`
- Literaturа: network risk propagation, social contagion models

**Metod:**

- Porivnyannya triogh pidkhodiv:
  1. Prostiproste seredne: $\bar{R} = \frac{1}{N}\sum R_i$
  2. Povazhene seredne (Burnout Index)
  3. Merezheva model' z sinkhronizatsiyeyu vidan'
- Eksperyment: yaka model' krashche prohnozyuye komandni risk eventy

**Rezultat:**

- Formal'na model' komandnoho ryzyku
- Porivnyal'na tablitsya triogh pidkhodiv

**Kryterii uspikhu:**

- Merezheva model' perevershuye prosto seredne za AUROC (delta ≥ preregistered margin)

**Riven' hotovnosti:** TRL 3 → TRL 5

---

## Д6 — Rozrobka alhorytmu

**Meta:** Realizuvaty optymizovanyy alhorytm yak doslidnytskyy prototip, okremyy vid production systemy.

**Vkhidni dani:**

- Rezultaty Д3 (CI dlya feasible state space)
- Rezultaty Д4 (optymalni vahy)
- Rezultaty Д5 (model komandnoho ryzyku)

**Metod:**

- Rozrobka research implementation (Python) iz viznachennymy interfeysamyinterfaces
- Versiyuvannya alhorytmu (alg-v1.0 — manual, alg-v2.0 — optimized)
- Dokumentuvannya API alhorytmu

**Rezultat:**

- Research implementation u Python
- Versionrovanyy alhorytm z testamy
- Opys API alhorytmu

**Kryterii uspikhu:**

- Alhorytm vidtvoryuye vsyi eksperymenty z Д7–Д8
- Unit-testuvannya ≥ 90% pokryttya

**Riven' hotovnosti:** TRL 4 → TRL 5

---

## Д7 — Eksperymental'na perevirka gipotez

**Meta:** Perevoryty H1–H5 na zadanyy danykh z vyznachenym protokolom.

**Vkhidni dani:**

- Labeled dataset (realni + syntetychni)
- Baseline modeli (Д8)
- Protokol: train/validation/test split, bootstrap CI

**Metod:**

- Dla kozhnoi gipotezy: vykonaty eksperyment, rozrakhuvaty metryki, zastosuvaty statystychni testy
- Korehnuvannya na mnozhinni porivnyannya (Benjamini-Hochberg)

**Rezultat:**

- Eksperymenta zvit z rezultatamy H1–H5
- Tablitsya: gipoteza → rezultat → p-value → vysnovok

**Kryterii uspikhu:**

- Kozha gipoteza maye statys (pryynyata / sprostovana / neznachushche)
- Nema gipotez iz statusom "vyznachyt' piznishe"

**Riven' hotovnosti:** TRL 5 → TRL 6

---

## Д8 — Porivnyannya z baseline

**Meta:** Dovesty, shcho zaproponovanyy metod perevershuye (abo ne perevershuye — tse tehy naukovy rezultat) bazovi pidkhody.

**Baseline modeli:**

1. Rule-only: stress ≥ 4.0 → high risk (chuynnyy production rule engine)
2. Population mean threshold: stress ≥ mean+1.5σ
3. Heuristic weighted score: potochnyy manual riskScore
4. Logistic regression (trained): klasychnyi ML baseline
5. Simple EWMA bez state vector

**Metryki dlya porivnyannya:**

- AUROC (zagal'na dyskryminatsiyna zdatnist')
- Calibration Error (tochnis' kalibruvannya)
- Precision@high-risk (tochnis' u sehmenti high-risk)
- False Positive Rate (khybno-pozytyvni)
- Brier Score (zagal'na yakist' imovimosteyj)

**Rezultat:**

- Porivnyal'na tablitsya vsikh modelei za vsima metrykami
- Ablatsiyni doslidzhennya: yak kozhen komponent vplyvaie na total

**Kryterii uspikhu:**

- Zaproponovanyi metod perevershuye ≥ 3 z 5 baselainiv za pryiorotyvnymy metrykami
- ABO: rezul'tat "ne krashshche" tehy naukovo zmistovnyy, yakshcho zafiksovanyi formalno

**Riven' hotovnosti:** TRL 5 → TRL 6

---

## Д9 — Prototip eksperymental'noyi platformy

**Meta:** Pobuduvaty viznachenu testovu platformu, yaka dozvolyaie:

- Zapuskaty eksperymenty iz riznymy konfiguratsiamy alhorytmu
- Loguvaty ta vidtvoryuvaty vsyi doslidzhennya
- Demonstruvaty result partner'am i revieweram

**Vkhidni dani:**

- Alhorytm z Д6
- Eksperymental'na metodolohiya z D7–D8

**Metod:**

- Pobydova experiment tracking pipeline (pytest + konfihuratsiyni fayly)
- Integratsia z nazvuyuchym DIP API

**Rezultat:**

- Prototip eksperymental'noyi platformy (Python + REST API)
- Experiment manifest dlya kozhnogo doslidzhennya

**Kryterii uspikhu:**

- Usyi eksperymenty z Д7-Д8 mozhy buty vidtvoreni z odnoho manifest-faylu

**Riven' hotovnosti:** TRL 5 → TRL 6

---

## Д10 — Validatsiya na real'nykh / syntetychnykh danykh

**Meta:** Validatsiya alhorytmu za umov, skhozhydnykh z real'nymy, iz urakhuvannyam etychnykh obmezhen'.

**Dani:**

- Syntetychni dani (pryorittet): CTGAN abo skhozhi modeli dlya generatsiyi realistychnykh behavioural time series
- Real'ni anonimiyzovani dani (pidmnozhyna, pislya etyky ta DMP approval)

**Metod:**

- Backtesting na syntetychnykh danykh iz vyznachemye rozpodiom
- Porivnyannya vykonannya na syntetychnykh vs real'nykh danykh (drift analysis)
- Out-of-distribution test: kohorty z atypovym baseline

**Rezultat:**

- Validatsiynyi zvit
- Reproduktsiyny paket (datasets, code, configs, artifacts)

**Kryterii uspikhu:**

- Kiyuvi metriky zberigayut' pryznacheiy porih (AUROC, CE) na ne peredbachuvani vybirtsi
- Coverage rate minimaksnykh intervaliv ≥ 90% (validatsiya Д3)

**Riven' hotovnosti:** TRL 6 → TRL 7

---

## Zvedennia etapiv

| Etap | Meta                  | Vkhid                | Rezultat                 | Kryterii          | TRL |
| ---- | --------------------- | -------------------- | ------------------------ | ----------------- | --- |
| Д1   | Formalizatsiya modeli | Kod, literatura      | Formalna spets.          | Aktseptovano KNU  | 2→3 |
| Д2   | Dynamika stanu        | Rivn. perekhodu      | Model $F(\mathbf{x}_t)$  | Identyfik. tip    | 2→3 |
| Д3   | Nevyznachenist'       | Marzheni, literaturа | CI metodolohiya          | Coverage ≥ 90%    | 3→4 |
| Д4   | Optymizatsiya vahiv   | Labeled outcomes     | $\hat{\mathbf{w}}$ iz CI | p<0.05, CV stable | 3→5 |
| Д5   | Komandnyy ryzyk       | Formuly, literatura  | Merezheva model'         | AUROC ≥ baseline  | 3→5 |
| Д6   | Alhorytm              | Д3, Д4, Д5           | Research impl.           | 90% test coverage | 4→5 |
| Д7   | Perevirka H1-H5       | Dataset, Д6          | Zvit H1-H5               | Usyi z statusom   | 5→6 |
| Д8   | Porivnyannya          | Д6, baselines        | Porivn. tablitsya        | ≥3/5 pereversheno | 5→6 |
| Д9   | Prototip              | Д6, Д7               | Exp. platforma           | Vidtvoryuvanist'  | 5→6 |
| Д10  | Validatsiya           | Syntet./real dani    | Valid. zvit              | Metryki ≥ porih   | 6→7 |

## Posylannya

- Related docs: A-scientific-problem-statement.md, C-experimental-methodology.md
- PARP Ścieżka SMART: https://www.parp.gov.pl/harmonogram-naborow/grants/sciezka-smart
- EIC Pathfinder: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
