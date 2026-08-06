# Explainability

## Document Metadata
- Owner: Explainable AI Lead
- Contributors: Product Research, ML Team, Decision Science Team
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити explainability framework для рішень DIP і представлення пояснень у Dzvin.co для різних аудиторій.

## Explainability Goals
- Пояснення мають допомагати приймати кращі рішення, а не лише пояснювати модель.
- Пояснення мають бути безпечними й недіагностичними.
- Пояснення мають бути auditable та відтворюваними.

## Audience Layers
- End-user: короткі, підтримуючі, non-clinical пояснення.
- Manager/HR: агреговані фактори ризику та рекомендовані дії.
- Admin/Research: детальні traces, confidence, policy source.

## Explanation Types
- Rule trace: які умови спрацювали.
- Feature rationale: які сигнали внесли найбільший вклад.
- Confidence context: рівень невизначеності.
- Policy rationale: чому обрано конкретний decision path.

## Minimum Explanation Contract
- decision_id
- explanation_summary
- top_contributing_signals
- confidence_level
- policy_variant
- timestamp
- model_or_rule_version

## Safety Constraints
- Заборонені категоричні клінічні формулювання.
- Обов'язкові обмеження інтерпретації (limitations).
- Escalation path для високого ризику і низької впевненості.

## Explainability Quality Criteria
- Faithfulness: пояснення відповідає реальному decision flow.
- Completeness: пояснення покриває ключові сигнали.
- Actionability: пояснення веде до зрозумілої дії.
- Stability: малі зміни у вході не створюють хаотичних пояснень.

## Technical Methods (Planned)
- Rule-native traces (implemented baseline).
- Contribution-based ranking for ML signals.
- Counterfactual-style "what changed" summaries.
- Segment-aware explanation templates.

## Validation Plan
- User comprehension testing.
- Trust uplift analysis vs no-explanation baseline.
- Error detection support study (чи помічають користувачі невпевнені рішення).

## Risks
- Over-explanation і когнітивне перевантаження.
- False sense of certainty.
- Leakage of sensitive attributes in explanations.

## Acceptance Criteria
- Кожне high-impact рішення має explainability payload.
- Пояснення відповідають role-based policy.
- Пояснення проходять safety review і user validation.

## Links
- Related docs: 16-decision-engine.md, 22-uncertainty.md, 29-explainability-validation.md, 37-ethics.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
