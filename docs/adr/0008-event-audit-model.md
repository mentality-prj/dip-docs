# ADR-0008: Event and Audit Model

Мова: Українська (default) | [English](0008-event-audit-model.en.md)

## Status

Accepted

## Context

The project requires auditable decision traces, experiment evidence and operational risk control.

## Options

1. Minimal logs only
2. Separate analytics store without audit guarantees
3. Structured event and audit model with immutable traces

## Decision

Structured event and audit model with immutable traces is adopted.

## Consequences

- Decision and policy changes can be replayed and reviewed.
- Audit volume and storage costs increase, but evidence quality improves.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
