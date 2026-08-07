# Scientific Hypotheses

Language: [Українська (default)](02-scientific-hypotheses.md) | English

## Purpose

Capture experimentally testable hypotheses for Dzvin.co + DIP.

## H1 Hybrid Decision Superiority

- Statement: Hybrid Rule+ML policy outperforms pure ML and rules-only on a composite quality/safety criterion.
- Primary metrics: AUROC, False alert rate, Disagreement resolution quality.
- Null hypothesis: there is no difference between the approaches.

## H2 Personal Baseline Advantage

- Statement: A personal adaptive baseline provides better calibration than a population baseline.
- Primary metrics: Calibration error, Brier score, segment stability.
- Null hypothesis: the personal baseline does not improve calibration.

## H3 Explainability Trust Uplift

- Statement: Role-aware explainability improves trust and action adoption.
- Primary metrics: Trust uplift, comprehension, adoption rate.
- Null hypothesis: explanation does not change user behavior.

## H4 Adaptive Feature Stability

- Statement: The adaptive feature set improves prediction stability under drift.
- Primary metrics: Drift resilience index, performance variance.
- Null hypothesis: adaptive features do not affect stability.

## H5 Governance Loop Safety

- Statement: Online policy governance with auto-mitigation reduces the duration of degraded periods.
- Primary metrics: degraded cycle duration, rollback frequency, safe-mode outcome quality.
- Null hypothesis: governance loops do not reduce operational risk.

## Acceptance Rule

- A hypothesis is accepted only if preregistered thresholds are met, with CI and effect size.
- Inconclusive data must be labeled `inconclusive`.

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
