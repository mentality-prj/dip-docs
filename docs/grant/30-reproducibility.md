# Reproducibility

Мова: Українська (default) | [English](30-reproducibility.en.md)

## Document Metadata
- Owner: Reproducibility Lead
- Contributors: Research Platform, ML Team, QA
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Забезпечити можливість повного повторення ключових результатів R&D і evaluation.

## Reproducibility Scope
- Data snapshots
- Feature versions
- Model/rule/policy versions
- Evaluation scripts and configs
- Output artifacts and reports

## Reproduction Protocol
1. Resolve target run/report id.
2. Restore exact dataset and feature snapshots.
3. Re-run pipeline with frozen config and seeds.
4. Compare metrics against tolerance bounds.
5. Generate reproducibility certificate.

## Environment Requirements
- Version-pinned dependencies.
- Infrastructure baseline definition.
- Deterministic settings where applicable.

## Tolerance Policy
- Exact match for deterministic modules.
- Bounded variance for stochastic components.
- Escalation on out-of-bound deltas.

## Audit Trail
- Who reproduced what and when.
- Comparison outputs and deviation notes.
- Root-cause analysis for mismatches.

## Acceptance Criteria
- Топ claims мають reproducibility certificates.
- Повторюваність перевіряється регулярно, не одноразово.
- Відхилення документуються з corrective actions.

## Links
- Related docs: 24-experiment-tracking.md, 25-evaluation.md, 12-statistics.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
