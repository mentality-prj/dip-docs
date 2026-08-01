# Scientific Hypotheses

## Мета
Зафіксувати експериментально перевірювані гіпотези для Dzvin.co + DIP.

## H1 Hybrid Decision Superiority
- Statement: Hybrid Rule+ML policy перевищує pure ML та rules-only за композитним критерієм quality/safety.
- Primary metrics: AUROC, False alert rate, Disagreement resolution quality.
- Null hypothesis: різниці між підходами немає.

## H2 Personal Baseline Advantage
- Statement: Personal adaptive baseline дає кращу калібрацію, ніж population baseline.
- Primary metrics: Calibration error, Brier score, segment stability.
- Null hypothesis: персональний baseline не покращує калібрацію.

## H3 Explainability Trust Uplift
- Statement: Role-aware explainability підвищує trust та action adoption.
- Primary metrics: Trust uplift, comprehension, adoption rate.
- Null hypothesis: пояснення не змінює поведінку користувача.

## H4 Adaptive Feature Stability
- Statement: Adaptive feature set підвищує стабільність прогнозу під drift.
- Primary metrics: Drift resilience index, performance variance.
- Null hypothesis: adaptive features не впливають на стабільність.

## H5 Governance Loop Safety
- Statement: Online policy governance з auto-mitigation зменшує тривалість degraded періодів.
- Primary metrics: degraded cycle duration, rollback frequency, safe-mode outcome quality.
- Null hypothesis: governance loops не зменшують операційний ризик.

## Рішення про прийняття
- Гіпотеза приймається лише за preregistered thresholds із CI та effect size.
- Непереконливі дані маркуються `inconclusive`.
