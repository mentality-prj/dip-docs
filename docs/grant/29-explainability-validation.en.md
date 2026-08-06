# Explainability Validation

Language: [Українська (default)](29-explainability-validation.md) | English

## Document Metadata
- Owner: Explainability Research Lead
- Contributors: UX Research, Data Science, Ethics Team
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Оцінити якість explainability outputs за критеріями faithfulness, clarity, actionability і safety.

## Validation Framework
- Technical faithfulness tests.
- User comprehension tests.
- Decision-support utility tests.
- Safety language audits.

## Faithfulness Tests
- Перевірка відповідності explanation до фактичного decision trace.
- Consistency checks across similar cases.
- Counterfactual sanity checks.

## Clarity and Utility Tests
- Time-to-understand metric.
- Correct interpretation rate.
- Recommendation-action linkage score.

## Safety Checks
- No diagnostic overclaim language.
- Uncertainty disclosures where needed.
- Harmful framing detection.

## Comparative Design
- With explanation vs without explanation.
- Full detail vs concise role-adapted explanation.

## Success Criteria
- Пояснення підвищують правильність інтерпретації.
- Пояснення не знижують safety outcomes.
- Пояснення покращують adoption у цільових ролях.

## Acceptance Criteria
- Explainability quality gates визначені і автоматизовані де можливо.
- Reviewer-ready report готується для кожного major release.
- Виявлені failure modes мають mitigation plan.

## Links
- Related docs: 20-explainability.md, 28-user-validation.md, 25-evaluation.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
