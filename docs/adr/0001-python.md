# ADR-0001: Python as DIP Core Language

Мова: Українська (default) | [English](0001-python.en.md)

## Status
Accepted

## Context
DIP потребує швидкого розвитку AI/ML integration, data pipelines і explainability tooling.

## Options
1. Python
2. TypeScript/Node.js
3. JVM stack

## Decision
Обрано Python для core DIP.

## Consequences
- Плюси: сильна AI/ML екосистема, швидкий R&D цикл.
- Мінуси: більше уваги до performance tuning у high-load API paths.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
