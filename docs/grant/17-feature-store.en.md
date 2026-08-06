# Feature Store

Language: [Українська (default)](17-feature-store.md) | English

## Document Metadata
- Owner: Data Platform Lead
- Contributors: ML Team, Backend Team, Analytics Team
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити архітектуру Feature Store для DIP + Dzvin.co як єдиного джерела ознак для rule/ML/analytics сценаріїв.

## Objectives
- Уніфікувати визначення feature між R&D і production.
- Забезпечити versioning, lineage і reproducibility.
- Мінімізувати train-serve skew.

## Core Principles
- Single semantic definition per feature.
- Explicit ownership і lifecycle.
- Time-aware computation (event time > processing time).
- Auditability і tenant isolation.

## Feature Taxonomy
- Behavioral: mood/stress/energy/focus dynamics.
- Engagement: activity frequency, streaks, drop-off risk.
- Psychometric: PHQ-9, GAD-7, PSS-4, K10 derived aggregates.
- Organizational: team volatility, participation ratios.
- Meta-features: completeness, freshness, confidence.

## Feature Entity Model
Кожна ознака має містити:
- feature_key
- display_name
- data_type
- unit
- computation_formula
- window
- source_collections
- null_policy
- quality_rules
- owner
- version

## Storage and Access Pattern
- Offline store: історичні обчислення для train/analysis.
- Online access layer: низька латентність для inference.
- Registry metadata: schema, ownership, lineage, quality status.

## Versioning Policy
- Semantic versioning для логіки обчислення.
- Major: несумісна зміна формули.
- Minor: розширення сумісної логіки.
- Patch: виправлення без зміни семантики.

## Quality Gates
Перед публікацією feature version:
- schema validation
- null/outlier checks
- drift check vs baseline
- reproducibility replay on reference dataset

## Train-Serve Consistency Controls
- Спільний computation contract для training та inference.
- Frozen feature sets per experiment/model version.
- Compatibility matrix: model version <-> feature version.

## Governance
- Feature owner (business + technical).
- Review board для high-impact features.
- Deprecation policy з grace period.

## Risks
- Feature explosion і некерована складність.
- Непрозора семантика ознак без data dictionary.
- Latency penalty для складних windowed features.

## Implementation Milestones
1. Feature catalog v1
2. Versioned computation specs
3. Quality monitoring dashboard
4. Online/offline parity checks

## Acceptance Criteria
- 100% production features мають metadata contract.
- Критичні features мають lineage і quality status.
- Для кожного model run існує reproducible feature snapshot.

## Links
- Related docs: 08-dataset-specification.md, 09-feature-engineering.md, 18-model-registry.md, 24-experiment-tracking.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
