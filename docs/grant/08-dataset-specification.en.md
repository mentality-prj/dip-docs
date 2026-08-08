# Dataset Specification

Language: [Українська (default)](08-dataset-specification.md) | English

## Document Metadata
- Owner: Data Governance Lead
- Contributors: Research Ops, Backend, Privacy Officer
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати набори даних для R&D та production decision support у Dzvin.co + DIP, їх походження, структуру і обмеження.

## Psychometric Instruments — Scientific Justification
Scale selection is grounded in validated clinical instruments:

| Instrument | Measures | Scientific basis |
|------------|----------|------------------|
| PHQ-9 | Depressive symptoms (9 items) | Kroenke et al., 2001; widely validated screening tool |
| GAD-7 | Generalised anxiety (7 items) | Spitzer et al., 2006; standard for anxiety screening |
| PSS-4 | Perceived stress (short form) | Cohen et al., 1983; validated short stress scale |
| K10 | General psychological distress | Kessler et al., 2002; population-level distress screening |

Note: instruments are used as **screening / signal**, not as diagnosis. Clinical interpretation requires human oversight (see 27-clinical-validation.md).

## Collection Frequency and Time-Series Structure
- Daily check-in: mood/stress/energy/focus (daily cadence, optional).
- Psychometric assessments: periodic (weekly/monthly cadence by configuration).
- Rolling windows: 7-day and 14-day moving averages; 30-day baseline window.
- Series structure: ordered sequence (event timestamp) with irregular intervals; missingness handled via freeze logic and recency decay.
- Minimum for inference: 30+ mood records for persona-level trajectory prediction.

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

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
