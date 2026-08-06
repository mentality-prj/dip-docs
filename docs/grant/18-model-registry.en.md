# Model Registry

Language: [Українська (default)](18-model-registry.md) | English

## Document Metadata
- Owner: MLOps Lead
- Contributors: ML Team, Platform Team, QA
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати Model Registry як контрольну площину життєвого циклу моделей, сумісну з DIP decision contract.

## Registry Entity
Кожен запис моделі містить:
- model_id
- version
- model_type
- training_dataset_snapshot
- feature_set_version
- evaluation_report_ref
- approval_status
- deployment_targets
- rollback_reference

## Lifecycle States
- Draft
- Validated
- Approved
- Deployed
- Deprecated
- Archived

## Approval Workflow
- Technical validation gate.
- Responsible AI and bias gate.
- Security/compliance gate.
- Final release approval.

## Deployment Governance
- Canary/limited rollout options.
- Policy-bound activation.
- Automatic rollback triggers.

## Compatibility Controls
- Model <-> feature version matrix.
- Model <-> policy configuration matrix.
- Backward compatibility status.

## Audit Requirements
- Immutable change history.
- Who/when/why for each state change.
- Linked evidence artifacts.

## Acceptance Criteria
- Жодна модель не деплоїться без approved registry record.
- Є простежуваність від моделі до evaluation/bias reports.
- Rollback сценарій задокументований для кожної deployed model.

## Links
- Related docs: 17-feature-store.md, 23-model-lifecycle.md, 24-experiment-tracking.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
