# Dataset Specification

Мова: Українська (default) | [English](08-dataset-specification.en.md)

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

## Psychometric Instruments — Scientific Justification

Вибір шкал обґрунтований валідованими клінічними інструментами:

| Instrument | Що вимірює                          | Наукова основа                                                   |
| ---------- | ----------------------------------- | ---------------------------------------------------------------- |
| PHQ-9      | Депресивна симптоматика (9 пунктів) | Kroenke et al., 2001; широко валідований скринінговий інструмент |
| GAD-7      | Генералізована тривога (7 пунктів)  | Spitzer et al., 2006; стандарт для anxiety screening             |
| PSS-4      | Сприйнятий стрес (коротка форма)    | Cohen et al., 1983; валідована коротка шкала стресу              |
| K10        | Загальний психологічний дистрес     | Kessler et al., 2002; population-level distress screening        |

Примітка: інструменти використовуються як **screening / signal**, не як діагноз. Клінічна інтерпретація потребує людського нагляду (див. 27-clinical-validation.md).

## Collection Frequency and Time-Series Structure

- Daily check-in: mood/stress/energy/focus (щоденна каденція, опційна).
- Psychometric assessments: періодично (тижнева/місячна каденція за конфігурацією).
- Rolling windows: 7-денне та 14-денне ковзні середні; 30-денний baseline window.
- Структура ряду: впорядкована послідовність (event timestamp) з нерівномірними інтервалами; missingness обробляється через freeze logic і recency decay.
- Мінімум для inference: 30+ mood-записів для persona-level trajectory prediction.

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
