# Data Quality

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
