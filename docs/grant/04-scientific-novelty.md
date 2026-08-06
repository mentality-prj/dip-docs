# Scientific Novelty

## Document Metadata
- Owner: Scientific Coordinator
- Contributors: ML Lead, Decision Science Lead, Product Research Lead
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft for reviewer-facing narrative

## Purpose
Сформулювати перевірювані наукові novelty claims для Dzvin.co + DIP і відділити вже підтверджені інженерні факти від гіпотез, що потребують експериментальної валідації.

## Reviewer-Oriented Summary
Інновація проєкту не в окремій моделі, а в architecture-level framework для пояснюваного прийняття рішень у чутливому домені: hybrid decision stack (rules + ML + policy governance) з auditability, online evaluation і адаптивною персоналізацією.

## Novelty Claim N1: Declarative Hybrid Decision Layer
### Claim
Рішення формується не тільки через black-box prediction, а через декларативну композицію:
- deterministic rules;
- ML/cohort signals;
- policy-tier conflict resolution;
- explicit fallback logic.

### Why non-obvious
Більшість систем реалізують або rules-only, або ML-only pipelines без формального шару узгодження політик у runtime.

### Evidence status
- Engineering baseline: частково реалізовано (rule evaluation, risk scoring, policy controls).
- Scientific validation: pending.

## Novelty Claim N2: Explainability as First-Class Decision Artifact
### Claim
Система повертає не лише risk score, а структуру пояснення (matched rules, confidence, policy source, diagnostic traces), придатну до аудиту.

### Why non-obvious
У багатьох production AI-системах explainability є post-hoc або UI-доповненням, а не частиною контракту рішення.

### Evidence status
- Engineering baseline: є trace/explanation outputs та admin diagnostics surfaces.
- Scientific validation: вплив на trust/adoption потребує контрольованих досліджень.

## Novelty Claim N3: Adaptive Risk via Multi-Signal Personalization
### Claim
Risk signal поєднує prediction probability, anomaly score, z-score та adaptive baseline states для різних цільових рівнів (company/team/user).

### Why non-obvious
Поєднання індивідуальних, командних і політичних сигналів із runtime governance рідко реалізується як єдина операційна система прийняття рішень.

### Evidence status
- Engineering baseline: є weighted risk composition, adaptive risk helpers, trust gating.
- Scientific validation: pending (потрібні абляції та статистичні тести).

## Novelty Claim N4: Built-in Online Evaluation and Self-Protection Loops
### Claim
Decision policy адаптується на основі online evaluation (A/B, drift, calibration, trust score), включно з auto-mitigation у degraded режимах.

### Why non-obvious
У типовому enterprise analytics циклі оцінка якості відбувається офлайн і не інтегрована з runtime policy control.

### Evidence status
- Engineering baseline: реалізовані trust thresholds, mitigation cycles, policy override audit.
- Scientific validation: pending (довести довгострокову стабільність і безпечність).

## Novelty Claim N5: Research-to-Production Traceability Pattern
### Claim
Один і той самий decision contract підтримує перехід від експерименту до production-інференсу без втрати інтерпретованості.

### Why non-obvious
Часто research pipelines і production pipelines розходяться, що знижує відтворюваність.

### Evidence status
- Engineering baseline: частково реалізований через platform/application separation.
- Scientific validation: pending multi-cycle reproducibility study.

## Testability Matrix
| Claim | Primary Test Type | Secondary Test Type | Main Endpoint/Artifact |
|---|---|---|---|
| N1 | Ablation (rules vs ML vs hybrid) | Robustness by cohort | Decision policy metrics |
| N2 | User trust experiment | Decision audit completeness | Explainability validation outputs |
| N3 | Calibration + AUROC by segment | Drift sensitivity | Risk signal components |
| N4 | Time-series policy health | Intervention safety checks | Online evaluation logs |
| N5 | Reproducibility protocol replay | Cross-env consistency | Experiment/decision trace |

## Falsifiability Conditions
Кожен claim вважається непідтвердженим, якщо:
- не досягнуті заздалегідь задані метрики;
- немає статистичної значущості у ключових порівняннях;
- результати не відтворюються в незалежних перезапусках.

## Boundaries and Responsible Framing
- Проєкт не заявляє медичну діагностику на цьому етапі.
- Результати позиціонуються як decision support, а не autonomous clinical judgement.
- Невизначеність і ліміти моделі мають бути явними у всіх high-impact сценаріях.

## Reviewer-Facing Acceptance Criteria
- Новизна сформульована як testable claims, а не маркетингові тези.
- Є чітке розділення між implemented baseline і expected research contribution.
- Для кожного claim визначено метод валідації та критерій відхилення.

## Links
- Related docs: 03-state-of-the-art.md, 05-research-questions.md, 06-methodology.md, 12-statistics.md, 29-explainability-validation.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
