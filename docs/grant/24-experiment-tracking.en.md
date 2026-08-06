# Experiment Tracking

Language: [Українська (default)](24-experiment-tracking.md) | English

## Document Metadata
- Owner: Research Platform Lead
- Contributors: ML Team, Data Team, QA
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити систему трекінгу експериментів для відтворюваності, аудиту і порівняння результатів.

## Minimum Run Metadata
- run_id
- hypothesis_id
- dataset_snapshot_id
- feature_set_version
- model/rule/policy versions
- random_seed
- metrics_summary
- artifact_uris
- author and timestamp

## Artifact Policy
- Immutable artifacts for published runs.
- Versioned storage for configs and outputs.
- Checksums for critical files.

## Experiment Taxonomy
- Exploratory runs
- Confirmatory runs
- Ablation runs
- Replication runs

## Promotion Rules
- Тільки confirmatory/replication runs можуть бути evidence для grant claims.
- Exploratory результати позначаються окремо.

## Reproducibility Checks
- One-click rerun from manifest.
- Cross-environment consistency check.
- Metric deviation tolerances.

## Auditability
- Change history for experiment definitions.
- Evidence linkage to evaluation reports.
- Access logs for sensitive artifacts.

## Acceptance Criteria
- 100% ключових висновків мають посилання на run artifacts.
- Replication runs доступні для reviewer-level audit.
- Tracking schema узгоджена з model registry.

## Links
- Related docs: 23-model-lifecycle.md, 25-evaluation.md, 30-reproducibility.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
