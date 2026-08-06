# Feature Engineering

## Document Metadata
- Owner: ML Engineering Lead
- Contributors: Data Platform, Research Scientists
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити підхід до проєктування, обчислення і валідації ознак для decision support та прогнозних моделей.

## Design Principles
- Кожна feature має бізнес-семантику.
- Формула має бути однозначною і відтворюваною.
- Ознака має бути доступною на inference time.
- Вразливі ознаки проходять bias review.

## Canonical Feature Card
- feature_key
- description
- type (numeric/categorical/boolean/text-derived)
- formula
- window (1d/7d/30d)
- source
- null policy
- expected range
- drift sensitivity

## Feature Families
- Trend features: slope, moving averages, volatility.
- Behavioral stability features: streaks, variance, recovery time.
- Psychometric aggregates: standardized subscales.
- Engagement features: recency/frequency/completion ratios.
- Team context features: peer baseline deltas.

## Example Candidate Features
- stress_average_7d
- mood_trend_14d
- energy_volatility_30d
- checkin_consistency_14d
- high_risk_team_ratio_30d
- psychometric_delta_30d

## Feature Transformation Rules
- Normalization by bounded scales.
- Winsorization for extreme outliers where justified.
- Encoding policy for low-cardinality categories.
- Missingness indicators for informative nulls.

## Data Leakage Controls
- Заборона використання future information.
- Time-based split discipline.
- Strict separation of label-period and feature-period.

## Feature Selection Strategy
- Baseline deterministic set.
- Model-driven relevance ranking.
- Stability selection across cohorts.
- Human review for interpretability and ethics.

## Monitoring
- Distribution drift per feature.
- Missingness drift.
- Correlation drift for critical feature pairs.

## Acceptance Criteria
- Для кожної production feature є feature card.
- Ознаки проходять leakage check і drift baseline check.
- Всі моделі мають зафіксований список feature versions.

## Links
- Related docs: 08-dataset-specification.md, 17-feature-store.md, 22-uncertainty.md, 26-metrics.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
