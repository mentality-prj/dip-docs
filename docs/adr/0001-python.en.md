# ADR-0001: Python as DIP Core Language

Language: [Українська (default)](0001-python.md) | English

## Status
Accepted

## Context
DIP requires rapid development of AI/ML integration, data pipelines, and explainability tooling.

## Options
1. Python
2. TypeScript/Node.js
3. JVM stack

## Decision
Python is selected as the core language for DIP.

## Consequences
- Pros: strong AI/ML ecosystem, fast R&D iteration cycle.
- Cons: requires extra attention to performance tuning in high-load API paths.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
