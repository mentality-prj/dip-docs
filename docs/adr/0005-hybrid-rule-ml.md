# ADR-0005: Hybrid Rule+ML Decision Policy

Мова: Українська (default) | [English](0005-hybrid-rule-ml.en.md)

## Status
Accepted

## Context
Rules-only недостатньо гнучкі, ML-only недостатньо прозорі для чутливого домену.

## Options
1. Rules-only
2. ML-only
3. Hybrid rule+ML with policy governance

## Decision
Вибрано hybrid rule+ML з trust-gated policy layer.

## Consequences
- Плюси: кращий баланс interpretability/quality/safety.
- Мінуси: вища складність оцінки та runtime governance.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
