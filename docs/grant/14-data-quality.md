# Data Quality

Мова: Українська (default) | [English](14-data-quality.en.md)

## Document Metadata
- Owner: Data Quality Lead
- Contributors: Data Platform, ML Team, Research Ops
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити framework контролю якості даних для стабільних рішень і коректної наукової валідації.

## Quality Dimensions
- Completeness
- Consistency
- Accuracy (where verifiable)
- Timeliness
- Uniqueness
- Validity

## Quality Rules
- Schema conformance checks.
- Mandatory field thresholds by dataset type.
- Range and logical constraints.
- Duplicate and anomaly detection.

## Quality Scoring
- Dataset-level quality score.
- Feature-level quality flags.
- Decision-time quality indicators.

## Missing Data Strategy
- Structured null taxonomy.
- Imputation only where methodologically justified.
- Missingness-aware model features.

## Drift and Freshness
- Freshness SLAs by data source.
- Drift alerts for critical distributions.
- Source outage and lag monitoring.

## Quality Incident Workflow
- Detection -> triage -> owner assignment -> remediation.
- Incident severity levels and deadlines.
- Post-incident root cause report.

## Acceptance Criteria
- Критичні pipelines мають automated quality gates.
- Quality status доступний для evaluation reports.
- Є historical quality dashboard для trend analysis.

## Links
- Related docs: 08-dataset-specification.md, 09-feature-engineering.md, 25-evaluation.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
