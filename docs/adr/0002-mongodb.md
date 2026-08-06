# ADR-0002: MongoDB for Flexible Domain and Event Data

## Status
Accepted

## Context
Потрібні гнучкі схеми для workflow, decision artifacts, audit/event records.

## Options
1. MongoDB
2. Relational-only approach
3. Hybrid polyglot storage from day one

## Decision
MongoDB використовується як primary operational store для поточного етапу.

## Consequences
- Плюси: schema flexibility, швидка ітерація доменної моделі.
- Мінуси: необхідні жорсткі governance правила для consistency і indexing.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
