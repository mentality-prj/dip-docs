# ADR-0009: DIP as Independent Product

## Status

Accepted

## Context

DIP must remain reusable across multiple products and domains, rather than becoming an internal module of Dzvin.co.

## Options

1. DIP embedded directly in Dzvin.co
2. DIP as internal library only
3. DIP as an independent platform product with public API boundaries

## Decision

DIP is maintained as an independent platform product.

## Consequences

- Clear separation between platform core and application layer.
- Easier reuse for future products and grant narratives.

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
