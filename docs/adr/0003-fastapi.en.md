# ADR-0003: FastAPI for DIP API Layer

Language: [Українська (default)](0003-fastapi.md) | English

## Status
Accepted

## Context
An API-first approach is needed with fast typed contract development and async readiness.

## Options
1. FastAPI
2. Flask
3. Django REST

## Decision
FastAPI is selected.

## Consequences
- Pros: Pydantic validation, async support, clear OpenAPI generation.
- Cons: requires discipline in backward compatibility for evolving contracts.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
