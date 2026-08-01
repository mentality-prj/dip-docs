# Model Registry

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
