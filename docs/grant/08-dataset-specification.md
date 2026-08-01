# Dataset Specification

## Document Metadata
- Owner: Data Governance Lead
- Contributors: Research Ops, Backend, Privacy Officer
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати набори даних для R&D та production decision support у Dzvin.co + DIP, їх походження, структуру і обмеження.

## Dataset Families
- User self-report events: mood, stress, energy, focus check-ins.
- Journal and story-derived signals: текстові індикатори (за політикою доступу).
- Psychometric assessments: PHQ-9, GAD-7, PSS-4, K10.
- Engagement/activity events: frequency, streaks, completion patterns.
- Organization-level aggregates: team/company risk and participation metrics.
- Decision artifacts: risk events, action recommendations, policy traces.

## Dataset Inventory Template
Для кожного dataset:
- dataset_id
- purpose
- owner
- source systems
- schema version
- refresh cadence
- retention
- lawful basis
- access scope

## Granularity Levels
- Individual level (restricted, privacy-sensitive).
- Team level (k-anonymity thresholds and masking).
- Company level (aggregated executive analytics).

## Temporal Properties
- Event timestamp
- Ingestion timestamp
- Feature window alignment
- Delay/missingness handling policy

## Inclusion and Exclusion Rules
- Minimum activity thresholds для model eligibility.
- Exclusion of corrupted/duplicated records.
- Masking of small cohorts for B2B outputs.

## Label-Readiness Criteria
- Достатня довжина історії.
- Мінімум валідних спостережень у вікні.
- Відсутність критичних data quality flags.

## Privacy and Security Controls
- Pseudonymization for research exports.
- Role-based access with least privilege.
- Audit logs for dataset access and exports.

## Known Limitations
- Self-report bias.
- Non-random missingness.
- Variable participation across teams/periods.

## Dataset Documentation Deliverables
- Data dictionary
- Lineage map
- Quality report per release
- Change log

## Acceptance Criteria
- 100% datasets мають owner, schema, retention і access policy.
- Є documented mapping dataset -> feature -> label -> model.
- Для кожного експерименту зафіксовано dataset snapshot id.

## Links
- Related docs: 09-feature-engineering.md, 10-label-definition.md, 11-ground-truth.md, 14-data-quality.md, 36-gdpr.md
