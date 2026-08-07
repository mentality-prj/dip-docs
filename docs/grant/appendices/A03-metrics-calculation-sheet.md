# A03 Metrics Calculation Sheet

Мова: Українська (default) | [English](A03-metrics-calculation-sheet.en.md)

## Purpose

Точний реєстр формул і порогів метрик, що використовуються в production-коді. Джерело — `mentality-back`.

## Code references

- `src/decision-support/helpers/burnout-index.calculator.ts`
- `src/decision-support/helpers/ml-risk.engine.ts`
- `src/decision-support/helpers/adaptive-risk.engine.ts`
- `src/decision-support/helpers/rule-engine.ts`
- `src/decision-support/helpers/impact-estimator.calculator.ts`
- `src/decision-support/decision-support-online-evaluation.service.ts`

---

## 1. Burnout Index

**Formula** (weighted sum, 0–100):

```
burnoutIndex =
  stress_norm × 30 +
  (1 − mood_norm) × 20 +
  (1 − energy_norm) × 20 +
  (1 − focus_norm) × 10 +
  high_risk_ratio × 15 +
  engagement_gap × 5
```

Where:

- `stress_norm = (avgStress − 1) / 4` (scale 1–5)
- `mood_norm = (avgMood − 1) / 4` (inverted: lower mood → higher score)
- `energy_norm = (avgEnergy − 1) / 4` (inverted)
- `focus_norm = (avgFocus − 1) / 4` (inverted)
- `high_risk_ratio = riskDistribution.high / totalEmployees`
- `engagement_gap = 1 − (activeEmployees / totalEmployees)`

**Levels:**
| Level | Condition |
|-------|-----------|
| high | burnoutIndex ≥ 60 |
| medium | 35 ≤ burnoutIndex < 60 |
| low | burnoutIndex < 35 |

**Factor triggers:**

| Factor                  | Trigger condition     |
| ----------------------- | --------------------- |
| high_stress             | stress_norm > 0.6     |
| low_mood                | (1−mood_norm) > 0.6   |
| low_energy              | (1−energy_norm) > 0.6 |
| low_focus               | (1−focus_norm) > 0.6  |
| high_risk_concentration | high_risk_ratio > 0.3 |
| low_engagement          | engagement_gap > 0.4  |

---

## 2. Composite Risk Score (riskScore)

**Formula:**

```
riskScore = (w_p × predictionProbability +
             w_a × anomalyScore +
             w_z × sigmoid(zScore)) / (w_p + w_a + w_z)
```

**Default weights:**
| Component | Weight |
|-----------|--------|
| predictionProbability | 0.55 |
| anomalyScore | 0.25 |
| zScore (sigmoid-normalized) | 0.20 |

`sigmoid(x) = 1 / (1 + e^−x)` — stabilizes extreme z-score values.

Output: `riskScore ∈ [0, 1]`

---

## 3. Prediction Probability (heuristic mode)

Rolling-window regression surrogate (no offline training required):

```
linear = −2.2
       + 1.1 × (stress_t − 3)
       + 0.7 × (stress_7d_avg − 3)
       + 0.6 × (stress_14d_avg − 3)
       + 0.8 × stress_delta
       + 0.9 × volatility
       − 0.5 × (mood_t − 3)

predictionProbability = sigmoid(linear)
```

**Features:**
| Feature | Description |
|---------|-------------|
| stress_t | Current stress level (1–5) |
| stress_7d_avg | 7-day rolling average stress |
| stress_14d_avg | 14-day rolling average stress |
| stress_delta | stress_t − stress_7d_avg |
| volatility | std-dev of recent stress values |
| mood_t | Current mood level (1–5) |

---

## 4. Anomaly Score

Isolation-heuristic approach:

```
expectedStress = (stress_7d_avg + stress_14d_avg) / 2
localDeviation = |stress_t − expectedStress|

weightedDeviation = localDeviation
                  + |stress_delta| × 0.7
                  + volatility × 0.8

anomalyScore = clamp(weightedDeviation / 3, 0, 1)
```

---

## 5. Z-Score (personalised baseline)

```
baseline.mean = mean(stress_30d_history)
baseline.std  = max(std(stress_30d_history), 0.15)   # floor prevents collapse

zScore = (currentStress − baseline.mean) / baseline.std
```

Baseline recomputed from the last 30 observations per user.

---

## 6. ML Trust Score

Weighted composite of four quality indicators:

```
mlTrust.accuracy     = accuracy × 0.40
mlTrust.calibration  = (1 − calibrationError) × 0.25
mlTrust.drift        = (1 − driftScore) × 0.20
mlTrust.coverage     = cohortCoverageScore × 0.15

weighted = mlTrust.accuracy + mlTrust.calibration
         + mlTrust.drift + mlTrust.coverage

mlTrustScore = clamp(weighted × samplePenalty, 0, 1)
```

**Classification:**
| Level | Condition |
|-------|-----------|
| low | mlTrustScore < 0.45 |
| medium | 0.45 ≤ mlTrustScore < 0.65 |
| high | mlTrustScore ≥ 0.65 |

Minimum conclusive sample for trust: 20 observations.

---

## 7. Drift Score

```
recentMean  = mean(predictedScores in last 7 days)
overallMean = mean(predictedScores in evaluation window, 30 days)

driftScore = clamp(|recentMean − overallMean|, 0, 1)
```

Alert threshold: `driftScore ≥ 0.20`

---

## 8. Calibration Error (Mean Absolute Error)

```
calibrationError = (1 / N) × Σ |predictedScore_i − actualScore_i|
```

Where `actualScore ∈ {0.0 (not_worsened), 0.5 (inconclusive), 1.0 (worsened)}`.

---

## 9. Rule Engine Thresholds

Deterministic rule conditions applied per team/company:

| Rule | Condition                                         | Action type       | Priority |
| ---- | ------------------------------------------------- | ----------------- | -------- |
| R-1  | avgStress ≥ 4.0 AND highRiskRatio > 40%           | team_intervention | high     |
| R-2  | mediumPlusRiskRatio > 25% AND highRiskRatio ≤ 40% | manager_alert     | medium   |
| R-3  | avgMood ≤ 2.5                                     | team_intervention | medium   |
| R-4  | avgEnergy ≤ 2.5                                   | manager_alert     | medium   |
| R-5  | avgFocus ≤ 2.5                                    | manager_alert     | low      |
| R-6  | activeEmployees / totalEmployees < 60%            | manager_alert     | medium   |
| R-7  | Company-wide avgStress ≥ 4.0                      | org_change        | high     |
| R-8  | Company-wide engagement < 60%                     | org_change        | high     |
| R-9  | stress ↔ GAD-7 correlation ≥ 0.7                  | org_change        | high     |
| R-10 | stress ↔ PHQ-9 correlation ≥ 0.7                  | org_change        | high     |

**Severity enrichment (baseline-aware):**

```
stressDelta = avgStress − prevAvgStress

severity = critical  if avgStress ≥ 4.0 AND highRiskRatio > 0.4 AND stressDelta ≥ 0.5
         = high      if avgStress ≥ 4.0 OR stressDelta ≥ 0.5
         = medium    if avgStress > 3.5 OR stressDelta ≥ 0.3
         = low       otherwise
```

**Signal confidence:**

```
engagement = activeEmployees / totalEmployees
confidence = 1.0  if totalEmployees ≥ 20 AND engagement ≥ 0.7
           = 0.8  if totalEmployees ≥ 20 OR engagement ≥ 0.7
           = 0.6  if totalEmployees ≥ 10
           = 0.4  otherwise
```

---

## 10. Business Impact Model (ROI Layer)

Piecewise-linear attrition probability by burnoutIndex:

```
attritionPct(index):
  index ∈ [0, 35)  →  2 + (index / 35) × (5 − 2)
  index ∈ [35, 60) →  5 + ((index − 35) / 25) × (12 − 5)
  index ∈ [60, 100]→  12 + ((index − 60) / 40) × (25 − 12)
```

Replacement cost:

```
replacementCostPerEmployee = avgAnnualSalary × replacementFactor

replacementFactor:
  junior → 0.40
  mid    → 0.75  (default)
  senior → 1.50

estimatedAttritionCost = activeEmployees × (attritionPct / 100) × replacementCostPerEmployee

avgMonthlySalary = avgAnnualSalary / 12
productivityLossMid = (productivityLossMin + productivityLossMax) / 2
estimatedProductivityLoss = activeEmployees × avgMonthlySalary × (productivityLossMid / 100)
```

**Productivity and sick-days table (source: Gallup, WHO, SHRM):**

| Burnout level | Productivity loss | Sick days increase |
| ------------- | ----------------- | ------------------ |
| low           | 0–5%              | +0–5%              |
| medium        | 5–12%             | +5–15%             |
| high          | 12–25%            | +15–30%            |

Default `avgAnnualSalary = €60,000`.

---

## 11. Adaptive Baseline (EWMA)

Exponentially weighted moving average for personalised baseline:

```
ewma_t = α × value_t + (1 − α) × ewma_{t−1}
```

Where `α = 0.38` (recency weight parameter).

**Weighted standard deviation with recency decay:**

```
weight_i = 0.92^(N − 1 − i)   # 0.92 = RECENCY_DECAY, i = position ascending
variance  = Σ(weight_i × (value_i − ewma)²) / Σ(weight_i)
std       = max(sqrt(variance), 0.18)   # floor = MIN_STD
```

**Baseline confidence:**

```
coverage  = clamp(n_samples / 10, 0, 1)
recency   = 1.00 if hours_since_last ≤ 48
          = 0.80 if hours_since_last ≤ 96
          = 0.60 otherwise
stability = 1 − clamp(volatility / 1.4, 0, 1)

confidence = clamp(0.20 + coverage × 0.40 + recency × 0.15 + stability × 0.25, 0.20, 0.95)
```

---

## 12. Risk Levels (individual, from riskScore)

| Level  | Condition               |
| ------ | ----------------------- |
| low    | riskScore < 0.38        |
| medium | 0.38 ≤ riskScore < 0.68 |
| high   | riskScore ≥ 0.68        |

Uncertainty classification:

```
uncertaintyLevel = high    if confidence < 0.45 OR uncertaintyCoefficient ≥ 1.15
                 = medium  if confidence < 0.70 OR uncertaintyCoefficient ≥ 0.70
                 = low     otherwise
```

---

## 13. Outcome Worsening Evidence (online evaluation)

Applied 7 days after a risk event prediction:

```
worsenedByDeltaAndVolatility:
  stressAfter − stressBefore ≥ 0.30   (WORSENING_STRESS_DELTA)
  AND stressVolatilityAfter ≥ 0.35    (WORSENING_VOLATILITY_THRESHOLD)

worsenedByMoodAndTrend:
  moodBefore − moodAfter ≥ 0.25       (WORSENING_MOOD_DELTA)
  AND sustainedWorseningDays ≥ 3      (WORSENING_SUSTAINED_DAYS)

actualOutcome = worsened     if worsenedByDeltaAndVolatility OR worsenedByMoodAndTrend
              = not_worsened otherwise
```

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
