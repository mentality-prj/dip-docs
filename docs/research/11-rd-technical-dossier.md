# R&D Technical Dossier

**Project:** Dzvin.co + Decision Intelligence Platform (DIP)
**Version:** 1.0 | **Date:** 2026-08-08 | **Status:** For Grant Application

Language: Українська (default) | [English](11-rd-technical-dossier.en.md)

---

## Chain of Evidence

```
Existing system
    ↓
Mathematical problem (limitations of heuristic baseline)
    ↓
Proposed method (state vector + minimax + hybrid governance)
    ↓
Scientific novelty (formalised claims N1–N5)
    ↓
Verification (hypotheses H1–H5 + evaluation protocol)
    ↓
Expected result (TRL 4→7, publications, platform reuse)
```

---

## 1. Опис продукту та проблема

### 1.1 Система

**Dzvin.co** — корпоративна платформа психічного здоров'я з архітектурою трьох шарів:

| Шар | Аудиторія      | Основні функції                                                                                    |
| --- | -------------- | -------------------------------------------------------------------------------------------------- |
| B2C | Pracівники     | Check-ins настрою (mood/stress/energy/focus 1–5), щоденник, афірмації, тести PHQ-9/GAD-7/PSS-4/K10 |
| B2B | HR / Менеджери | Агрегована аналітика, risk events, decision support reports                                        |
| R&D | Internal ML    | Risk scoring, trajectory prediction, online evaluation                                             |

**Decision Intelligence Platform (DIP)** — незалежна платформа: rule evaluation, prediction, explainability, audit. Dzvin.co інтегрується з DIP через API-контракт.

### 1.2 Поточний стан MVP (TRL 4–6)

**Реалізовано:**

- REST API рушій правил та рішень (FastAPI, Python)
- Rule engine — 10 детермінованих правил з baseline-aware severity
- Burnout Index (0–100) на основі 6 факторів із зваженими відступами
- Composite Risk Score — три сигнали (prediction, anomaly, z-score) з вагами
- Adaptive Baseline Engine — EWMA α=0.38 з recency decay
- State Vector + Feasible State Space + best/worst-case bounds
- System stability score
- ML Trust Score (accuracy/calibration/drift/coverage)
- Online evaluation: A/B policy, drift detection, auto-mitigation
- MongoDB event store + audit log
- NestJS backend: B2C + B2B + R&D surfaces
- OpenAI integration: AI-generated executive summaries

**Евристичні компоненти (потребують R&D):**

- Prediction probability — surrogate логістична регресія без offline training
- Ваги state risk (0.34/0.22/0.18/0.16/0.10) — встановлені вручну
- Коефіцієнти EWMA (α=0.38, decay=0.92) — не оптимізовані
- Best/worst-case margins — консервативні апроксимації
- Зв'язок між PHQ-9/GAD-7 і risk score — не верифікований клінічно

### 1.3 Математична проблема

Поточна система використовує **фіксовані ваги та пороги**, незалежні від:

- розподілу популяції користувачів;
- часової динаміки окремого користувача;
- міжіндивідуальної варіабельності психометричних шкал.

Це призводить до:

- false positives у когортах з хронічно підвищеним базовим рівнем стресу;
- нестабільних прогнозів при drift вхідних розподілів;
- відсутності формальних гарантій safety для high-impact рішень.

**Дослідницька задача:** побудувати теоретично обґрунтовану модель, де ваги, пороги та policy є похідними від даних, а не від ручного налаштування.

---

## 2. Алгоритмічна специфікація (верифіковані формули)

### 2.1 Вектор стану користувача

Поточний стан $i$-го користувача в момент $t$:

$$\mathbf{x}_t = \begin{pmatrix} s_t \\ m_t \\ \sigma_t \\ r_t \\ \zeta_t \end{pmatrix}$$

Де:

- $s_t$ — stress ∈ [1,5]
- $m_t$ — mood ∈ [1,5]
- $\sigma_t$ — volatility (std нещодавніх спостережень стресу)
- $r_t$ — recovery rate ∈ [0,1]
- $\zeta_t$ — social stability ∈ [0,1]

**Recovery rate** (з коду `adaptive-risk.engine.ts`):

```
recoverySignal    = Σ max(0, −Δstress) × 0.6 + max(0, Δmood) × 0.4
degradationSignal = Σ max(0, +Δstress) × 0.55 + max(0, −Δmood) × 0.45
r_t = clamp((recoverySignal + 0.1) / (recoverySignal + degradationSignal + 0.2), 0, 1)
```

**Social stability:**

```
ζ_t = clamp(cadenceRegularity × 0.55 + (1 − σ_norm) × 0.25 + confidence × 0.20, 0, 1)
```

### 2.2 Персоналізований baseline (EWMA)

Очікуване значення стресу через EWMA:

$$\hat{s}_t = \alpha \cdot s_t + (1 - \alpha) \cdot \hat{s}_{t-1}, \quad \alpha = 0.38$$

Зважений стандартний відхил з recency decay:

$$\hat{\sigma}_t = \max\!\left(\sqrt{\frac{\sum_{i} \rho^{N-1-i}(s_i - \hat{s}_t)^2}{\sum_{i} \rho^{N-1-i}}}, \; 0.18\right), \quad \rho = 0.92$$

Confidence baseline:

```
confidence = clamp(0.20 + coverage × 0.40 + recency × 0.15 + stability × 0.25, 0.20, 0.95)
```

### 2.3 Допустимий простір станів (Feasible State Space)

Для кожної виміру $d$:

$$\mathcal{F}_d = [\mathbf{x}_t^{(d)} - \Delta_d, \; \mathbf{x}_t^{(d)} + \Delta_d]$$

Де margin $\Delta_d$ залежить від confidence interval та confidence:

```
Δ_stress    = max((CI_upper − CI_lower) / 2, 0.18)
Δ_mood      = max((CI_upper − CI_lower) / 2, 0.18)
Δ_volatility = clamp(σ × 0.22 + (1 − conf) × 0.40, 0.06, 0.80)
Δ_recovery  = clamp((1 − conf) × 0.30 + σ × 0.04, 0.05, 0.35)
Δ_social    = clamp((1 − conf) × 0.28 + σ × 0.03, 0.05, 0.30)
```

### 2.4 Best-case / Worst-case (мінімакс оцінювання)

```
best_case  = argmin_{x ∈ F} risk(x) → {s_min, m_max, σ_min, r_max, ζ_max}
worst_case = argmax_{x ∈ F} risk(x) → {s_max, m_min, σ_max, r_min, ζ_min}
```

Risk evaluation for a given state vector:

$$\text{stateRisk} = 0.34 \cdot s_{\text{norm}} + 0.22 \cdot (1-m_{\text{norm}}) + 0.18 \cdot \sigma_{\text{norm}} + 0.16 \cdot (1-r) + 0.10 \cdot (1-\zeta)$$

$$\text{deviationRisk} = \sigma\!\left(\frac{\text{deviationScore}}{1.6} \cdot 3 - 1.2\right)$$

$$\text{predictedRisk} = 0.45 \cdot \text{stateRisk} + 0.55 \cdot \text{deviationRisk}$$

### 2.5 Deviation Score

$$\text{deviationScore} = 0.8 \cdot \frac{|s_t - \hat{s}|}{\hat{\sigma}} + 0.2 \cdot \frac{|m_t - \hat{m}|}{\Delta_m}$$

### 2.6 Оцінка стабільності системи

$$\text{systemStability} = \text{clamp}\!\left(1 - \underbrace{0.4 \cdot \text{stateDrift}}_{\text{state change}} - \underbrace{0.35 \cdot (R_{\text{worst}} - R_{\text{best}})}_{\text{uncertainty envelope}} - \underbrace{0.15 \cdot \sigma_{\text{norm}}}_{\text{volatility}} + \underbrace{0.12 \cdot r + 0.08 \cdot \zeta}_{\text{resilience}}, 0, 1\right)$$

### 2.7 Composite Risk Score

$$\text{riskScore} = \frac{0.55 \cdot P_{\text{pred}} + 0.25 \cdot P_{\text{anomaly}} + 0.20 \cdot \sigma(\text{zScore})}{0.55 + 0.25 + 0.20}$$

Де:

| Component            | Formula                                                                       |
| -------------------- | ----------------------------------------------------------------------------- | ------------ | ----- | --- | ------------------- |
| $P_{\text{pred}}$    | `sigmoid(−2.2 + 1.1(s−3) + 0.7(s̄₇−3) + 0.6(s̄₁₄−3) + 0.8Δs + 0.9σ − 0.5(m−3))` |
| $P_{\text{anomaly}}$ | `clamp((                                                                      | s−s̄_expected | + 0.7 | Δs  | + 0.8σ) / 3, 0, 1)` |
| $\text{zScore}$      | `(s_t − baseline.mean) / max(baseline.std, 0.15)`                             |

### 2.8 ML Trust Score

$$\text{mlTrustScore} = \text{clamp}\!\left(\left[0.40 \cdot \text{acc} + 0.25 \cdot (1 - \text{cal}) + 0.20 \cdot (1 - \text{drift}) + 0.15 \cdot \text{cov}\right] \cdot \text{samplePenalty}, \; 0, 1\right)$$

### 2.9 Поширення ризику на командний рівень

Агрегація state vectors по команді:

$$\bar{\mathbf{x}}_{\text{team}} = \frac{1}{N}\sum_{i=1}^{N} \mathbf{x}_t^{(i)}$$

Team coupling bonus (синхронізація відхилень):

```
teamSyncDeviation = mean(|stressDeviation_i − mean_deviation| for each i)
if teamSyncDeviation < 0.7:
    synergy_bonus = (1 − teamSyncDeviation) × 0.25
```

Burnout Index (командний рівень):

$$\text{BI}_{\text{team}} = 0.30 \bar{s}_{\text{norm}} + 0.20(1-\bar{m}_{\text{norm}}) + 0.20(1-\bar{e}_{\text{norm}}) + 0.10(1-\bar{f}_{\text{norm}}) + 0.15 h_{\text{ratio}} + 0.05 e_{\text{gap}}$$

---

## 3. Науково-технічна новизна

### N1 — Декларативний hybrid decision layer

**Твердження:** Рішення виробляється через декларативну композицію:

```
rules → signal aggregation → policy-tier conflict resolution → explanation artifact
```

На відміну від типових систем, де ML-only або rules-only, тут обидва сигнали формально узгоджуються через policy governance зі строгим conflict resolution.

**Evidence status:** Engineering baseline реалізовано. Кількісне порівняння з alternatives — pending (H1).

### N2 — Explainability як частина contract

**Твердження:** Кожне high-impact рішення повертає:

- matched rules + conditions count
- feature-level contribution (deviation score, stressDeviation, moodDeviation)
- confidence context (mlTrustScore, uncertainty level)
- policy source and variant

Це не post-hoc UI, а частина decision API contract.

### N3 — Adaptive multi-signal risk (N-dimensional)

**Твердження:** Замість scalar threshold система оперує:

- 5-dimensional state vector $\mathbf{x}_t$
- feasible state space $\mathcal{F}$ зі строгими margins
- minimax risk bounds $[R_{\text{best}}, R_{\text{worst}}]$
- system stability measure

### N4 — Online policy self-protection

**Твердження:** Policy автоматично знижує вплив ML при drift:

```
if degraded_cycles ≥ 2 → safe-mode (rules_only)
if healthy_cycles ≥ 3 → restore hybrid
```

Усі зміни логуються з reason, source, TTL.

### N5 — Research-to-production traceability

**Твердження:** Той самий decision contract підтримує: offline experiment → controlled rollout → production inference. Трасування: dataset snapshot → feature version → policy state → decision audit.

---

## 4. Обмеження поточної моделі

| Компонент                          | Поточний статус                                     | Необхідна R&D                                              |
| ---------------------------------- | --------------------------------------------------- | ---------------------------------------------------------- |
| Prediction probability             | Surrogate heuristic; коефіцієнти встановлені вручну | Offline training на реальних траєкторіях; cross-validation |
| State risk weights (0.34/0.22/...) | Manual calibration                                  | Optimization (e.g. Bayesian, gradient) on outcome data     |
| EWMA α та decay                    | Фіксовані; не оптимізовані під популяцію            | Per-cohort hyperparameter search                           |
| Feasible space margins             | Conservative approximation                          | Empirical credible intervals з clinical validation         |
| PHQ-9/GAD-7 → risk mapping         | Not wired in pipeline (rules 9–10 not active)       | Clinical concordance study                                 |
| Team risk propagation              | Heuristic coupling bonus                            | Network analysis + causal modeling                         |
| Minimax → intervention             | No direct mapping                                   | Decision theory formalization                              |

---

## 5. Докази працездатності (поточні)

### 5.1 Система виконує всі детерміновані правила

Rule engine R1–R8 активовані в production pipeline. R9–R10 (GAD-7/PHQ-9 correlations) визначені, але потребують wiring.

### 5.2 Decision Engine повертає структурований output

Приклад decision response (синтетичний):

```json
{
  "decision": "high_risk",
  "rule": "R-1: avgStress ≥ 4.0 AND highRiskRatio > 40%",
  "matched_conditions": 2,
  "total_conditions": 2,
  "confidence": 0.8,
  "explanation": ["rule=R-1", "matched=2/2"]
}
```

### 5.3 Online evaluation pipeline активний

- A/B routing за fingerprint реалізований
- Degraded cycle detection + auto-mitigation реалізовані
- Trust thresholds (0.45 / 0.65) застосовуються в runtime

### 5.4 Burnout Index — чисельний приклад

Команда: avgStress=3.8, avgMood=2.8, avgEnergy=2.6, avgFocus=3.0, highRisk=30%, engagement=70%

```
stress_norm = (3.8−1)/4 = 0.70
mood_norm   = (2.8−1)/4 = 0.45 → inverted = 0.55
energy_norm = (2.6−1)/4 = 0.40 → inverted = 0.60
focus_norm  = (3.0−1)/4 = 0.50 → inverted = 0.50
high_risk_ratio = 0.30
engagement_gap  = 0.30

BI = 0.70×30 + 0.55×20 + 0.60×20 + 0.50×10 + 0.30×15 + 0.30×5
   = 21 + 11 + 12 + 5 + 4.5 + 1.5 = 55 → level: medium
```

### 5.5 Risk Score — чисельний приклад

User: stress_t=4.2, stress_7d_avg=3.5, stress_14d_avg=3.2, stress_delta=0.7, volatility=0.9, mood_t=2.5, baseline.mean=3.0, baseline.std=0.5

```
linear = −2.2 + 1.1×(4.2−3) + 0.7×(3.5−3) + 0.6×(3.2−3) + 0.8×0.7 + 0.9×0.9 − 0.5×(2.5−3)
       = −2.2 + 1.32 + 0.35 + 0.12 + 0.56 + 0.81 + 0.25 = 1.21
P_pred = sigmoid(1.21) ≈ 0.77

expectedStress = (3.5 + 3.2) / 2 = 3.35
localDeviation = |4.2 − 3.35| = 0.85
weightedDeviation = 0.85 + |0.7|×0.7 + 0.9×0.8 = 0.85 + 0.49 + 0.72 = 2.06
P_anomaly = clamp(2.06/3, 0, 1) = 0.69

zScore = (4.2 − 3.0) / 0.5 = 2.4
sigmoid(2.4) = 0.917

riskScore = (0.55×0.77 + 0.25×0.69 + 0.20×0.917) / 1.0
           = (0.424 + 0.173 + 0.183) = 0.780 → high risk
```

---

## 6. Архітектура системи

```
Dzvin.co (NestJS/TypeScript)
    │
    ├── B2C: mood check-ins → PHQ-9/GAD-7/K10 → AI summaries
    ├── B2B: aggregated analytics → decision support reports
    └── R&D: ML scoring → online evaluation → policy governance
            │
            ↓ REST API (x-api-key, tenant-scoped)
Decision Intelligence Platform (DIP)
    │
    ├── Rule Engine   (deterministic, 10 rules)
    ├── ML Engine     (heuristic + logistic regression + random forest)
    ├── Adaptive Risk (EWMA baseline + state vector + minimax)
    ├── Decision Audit (event store, trace, reproducibility)
    └── Policy Layer  (trust gating, A/B, auto-mitigation)
            │
            ↓
    MongoDB + audit log
```

**Integration contract:** decision API, workflow by ID or inline, sync/async modes, tenant-isolated.

**Tech stack:** Python/FastAPI (DIP), TypeScript/NestJS (Dzvin.co), MongoDB, OpenAI GPT-4.1, Zitadel OIDC.

---

## 7. Запропоновані методи та дослідницька програма

### 7.1 Обґрунтування ваг state risk через optimization

**Мета:** замінити ручно встановлені ваги (0.34/0.22/0.18/0.16/0.10) оптимальними.

**Метод:** мінімізація очікуваної calibration error по тренувальній вибірці:

$$\hat{\mathbf{w}} = \arg\min_{\mathbf{w}} \mathbb{E}\left[\left|\text{riskScore}(\mathbf{w}) - Y_{\text{actual}}\right|\right] \quad \text{s.t.} \quad \sum w_i = 1, w_i \geq 0$$

**Очікуваний результат:** calibration error < 0.15 (зараз не вимірюється систематично).

### 7.2 Formal confidence intervals для feasible state space

**Мета:** замінити консервативні margins емпіричними credible intervals.

**Метод:** Bootstrap confidence intervals зі стратифікацією по когортах. Margin $\Delta_d = t_{0.95} \cdot \hat{\sigma}_d / \sqrt{n}$.

### 7.3 Data-driven EWMA hyperparameters

**Мета:** оптимізувати α та ρ per cohort.

**Метод:** grid search з leave-one-out cross-validation на 30-денних window sequences. Оцінка: mean squared error між EWMA і actual next-day stress.

### 7.4 Clinical concordance: PHQ-9/GAD-7 → risk activation

**Мета:** активувати правила R9–R10, верифікувати correlation threshold 0.7.

**Метод:** Spearman correlation між normalized PHQ-9/GAD-7 scores та rolling stress series. Bootstrapped CI для порогового значення.

### 7.5 Team risk propagation model

**Мета:** формалізувати coupling bonus за мережевою структурою.

**Метод:** Graph-based aggregation з ваговими коефіцієнтами для manager-peer та peer-peer зв'язків.

---

## 8. Гіпотези та верифікація

| ID  | Гіпотеза                                     | Primary metrics                        | Test method                     | Null               |
| --- | -------------------------------------------- | -------------------------------------- | ------------------------------- | ------------------ |
| H1  | Hybrid Rule+ML > pure ML або rules-only      | AUROC, False alert rate                | Offline ablation (EXP-HYB-002)  | No difference      |
| H2  | Personal baseline > population baseline      | Calibration error, Brier score         | Segment comparison (EXP-AB-001) | No improvement     |
| H3  | Explainability підвищує trust та adoption    | Trust uplift, comprehension            | User study (EXP-XAI-003)        | No behavior change |
| H4  | Adaptive features стабільніші під drift      | Drift resilience index                 | Drift simulation (EXP-004)      | No stability gain  |
| H5  | Governance loops скорочують degraded periods | Degraded cycle duration, rollback rate | Time-series audit (EXP-GOV-004) | No safety benefit  |

**Критерії прийняття:** preregistered thresholds з CI та effect size. Непереконливі результати → `inconclusive`, не `positive`.

---

## 9. Валідаційний план

### 9.1 Offline evaluation

- Baseline моделі: deterministic rules, heuristic scoring, current production policy
- Метрики: AUROC, AUPRC, Calibration Error, Brier Score, Precision@top-10%
- Підхід: time-based split (training < cutoff, testing ≥ cutoff), no leakage

### 9.2 Online controlled evaluation

- A/B routing за user fingerprint (10% variant B)
- 7-day outcome window: worsening = Δstress ≥ 0.30 AND volatility ≥ 0.35
- Drift detection: |recentMean − overallMean| ≥ 0.20 → alert
- Auto-mitigation: degraded_cycles ≥ 2 → rules-only; recovery after 3 healthy cycles

### 9.3 Explainability validation

- Comprehension test: correct interpretation ≥ 80% (target NFR-004)
- Trust uplift: ≥ +10% vs no-explanation cohort (target NFR-005)
- Safety audit: no diagnostic overclaim language

### 9.4 Clinical plausibility

- Concordance з PHQ-9/GAD-7 scores де доступні
- Review escalation paths для high risk + low confidence
- Human oversight policy для high-impact decisions

---

## 10. Трасованість (Traceability Summary)

| RQ  | Hypothesis | Experiment  | Metrics                 | Scientific Claim                     |
| --- | ---------- | ----------- | ----------------------- | ------------------------------------ |
| RQ1 | H2         | EXP-AB-001  | Calibration error       | Personal baseline improves precision |
| RQ2 | H1         | EXP-HYB-002 | AUROC, false alert rate | Hybrid improves accuracy/safety      |
| RQ3 | H3         | EXP-XAI-003 | Trust uplift            | Explanations improve adoption        |
| RQ4 | H4         | EXP-004     | Drift resilience        | Adaptive features improve stability  |
| RQ5 | H5         | EXP-GOV-004 | Degraded duration       | Governance loops reduce risk         |

---

## 11. План розвитку (12–24 місяці)

| Milestone                        | Термін | Deliverable                                     | TRL |
| -------------------------------- | ------ | ----------------------------------------------- | --- |
| M1 — Protocol freeze             | M3     | Feature spec, dataset spec, evaluation protocol | 4→5 |
| M2 — Hybrid v1 validated         | M6     | Offline ablation report, H1 status              | 5   |
| M3 — Adaptive baseline optimized | M9     | Per-cohort α/ρ, H2 status                       | 5→6 |
| M4 — Clinical concordance        | M12    | PHQ-9/GAD-7 wiring, R9–R10 activated            | 6   |
| M5 — Online governance proven    | M15    | H5 status, policy stability audit               | 6→7 |
| M6 — Pilot evidence package      | M18    | Pilot outcomes, reproducibility dossier         | 7   |
| M7 — Platform reuse case         | M24    | Second-domain DIP integration, H5 replication   | 7   |

**Цільовий TRL:**

- DIP decision governance stack: TRL 6–7
- Explainability framework: TRL 6–7
- Dzvin.co integration: TRL 7

---

## 12. Очікувані наукові результати

- 2+ peer-reviewed publications або preprints (adaptive risk modeling, hybrid decision governance)
- Open algorithm specification для state-vector-based risk assessment
- Reproducibility pack для кожного з H1–H5 (datasets, code, artifacts)
- Technical whitepaper для practitioners (HR/wellbeing domain)

---

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal: https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ: https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form: https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
