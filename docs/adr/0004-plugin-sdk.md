# ADR-0004: Plugin SDK for Extensibility

Мова: Українська (default) | [English](0004-plugin-sdk.en.md)

## Status
Accepted

## Context
Потрібно масштабувати DIP без модифікації core при додаванні доменних або ML capabilities.

## Options
1. Plugin SDK with manifest and capability model
2. Direct in-core module additions
3. External sidecar-only integration

## Decision
Вибрано Plugin SDK підхід.

## Consequences
- Плюси: контрольована extensibility, швидше domain scaling.
- Мінуси: складніша governance модель (compatibility, security review, deprecation path).

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
