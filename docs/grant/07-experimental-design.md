# Experimental Design

Мова: Українська (default) | [English](07-experimental-design.en.md)

## Document Metadata
- Owner: Experimentation Lead
- Contributors: ML Team, Research Ops, Product Analytics
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати експериментальний дизайн для перевірки RQ щодо якості рішень, персоналізації, explainability та policy governance.

## Canonical Flow
Participants / Cohorts
-> Data Collection
-> Feature Engineering
-> Model/Rule Execution
-> Evaluation
-> Comparison
-> Publication / Internal Report

## Experiment Types
- Offline ablation (rules-only vs ML-only vs hybrid).
- Policy A/B for runtime decision strategies.
- Explainability UX experiments.
- Segment robustness experiments.

## Cohort Definition
- Company-level cohorts by size/industry.
- Team-level cohorts by engagement and volatility.
- Individual cohorts by activity and baseline stability.

## Randomization Strategy
- Fingerprint-based routing for policy variants.
- Stratified allocation for key cohorts.
- Guardrails for high-risk populations.

## Time Windows
- Observation window: historical baseline.
- Evaluation window: fixed post-decision horizon.
- Drift monitoring window: rolling intervals.

## Controls
- Holdout groups where ethically acceptable.
- Frozen baseline policy for comparison.
- Version-locked feature/model sets.

## Primary Outcomes
- Decision accuracy proxy.
- Action precision for high-risk cohorts.
- Trust and adoption impact for explained vs unexplained outputs.

## Secondary Outcomes
- Latency and operational overhead.
- Alert fatigue indicators.
- Stability under distribution shift.

## Threats to Validity
- Selection bias in participation.
- Non-stationary behavior patterns.
- Contamination between cohorts.

## Mitigation
- Stratification + reweighting.
- Sensitivity analyses.
- Protocol deviations log.

## Acceptance Criteria
- Кожен експеримент має preregistered hypothesis.
- Є визначені success/failure thresholds.
- Результати можна повторити за протоколом.

## Links
- Related docs: 05-research-questions.md, 06-methodology.md, 25-evaluation.md, 30-reproducibility.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
