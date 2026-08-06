# DIP Architecture

Мова: Українська (default) | [English](15-dip-architecture.en.md)

## Document Metadata
- Owner: Platform Architect
- Contributors: Backend Lead, ML Lead, DevOps Lead
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft aligned with current implementation baseline

## Purpose
Описати архітектуру DIP як platform core для decision intelligence та показати зв'язок між research-компонентами і production використанням у Dzvin.co.

## Architecture Goal
DIP має надавати доменно-агностичний набір сервісів для:
- формування рішень;
- пояснення рішень;
- контролю якості рішень у часі;
- безпечної інтеграції з domain applications.

## High-Level Topology
Application (Dzvin.co)
-> Adapter / Integration Layer
-> DIP API Surface
-> Decision and Intelligence Engines
-> Stores and Audit Infrastructure

## Layered View

### 1) Interface Layer
- REST endpoints для decision/prediction/workflow execution.
- API-key / tenant-aware access controls.
- Input validation і contract-level error handling.

### 2) Application Orchestration Layer
- Workflow orchestration.
- Job execution sync/async.
- Routing до rule/prediction components.

### 3) Domain Intelligence Layer
- Rule and workflow entities.
- Decision output contract: decision, matched conditions, actions, explanation, confidence (where available).
- Trace objects для reproducibility.

### 4) Data and State Layer
- Workflow definitions and related metadata.
- Event storage for decision events.
- Audit repository for decision execution trace.
- Optional model/feature registries in extended roadmap.

### 5) Governance and Observability Layer
- Audit trails.
- Policy controls and diagnostics integration points.
- Monitoring metrics and incident hooks.

## Integration Contract with Dzvin.co
Принципи інтеграції:
- комунікація через публічні API, без прямого доступу до internal DIP storage;
- tenant-scoped execution контекст;
- явне передавання feature payload і workflow selection;
- повернення структурованих decision artifacts для B2B/B2C surfaces.

## Current Baseline Capabilities (Verified)
- Workflow/rule evaluation endpoint із trace.
- Decision events and audit records.
- Prediction endpoint з deterministic fallback mode.
- Async job pattern для decision execution.
- RBAC/permission hooks для decision execution.

## Planned R&D Extensions
- Feature store versioning and lineage.
- Model registry governance (approval/rollback lifecycle).
- Drift detection and automated retraining triggers.
- Unified experiment tracking bridge.
- Plugin SDK hardening for third-party extensions.

## Security and Privacy by Design
- Tenant isolation at request handling and repository access.
- Principle of least privilege for decision execution.
- Auditable decision logs for post-hoc review.
- Minimized payload persistence where possible.

## Failure Modes and Fallback Strategy
- Workflow not found: explicit error and no silent fallback.
- Missing or low-quality features: confidence degradation path.
- External intelligence unavailable: deterministic fallback route.
- Policy disagreement: routed through governance tier.

## Research-to-Product Traceability
Кожен production-рішення має бути трасованим до:
- workflow/rule version;
- feature snapshot;
- policy state;
- evaluation status (when enabled).

Це критично для грантової валідації, auditability і відтворюваності.

## Architecture Decisions to Lock
- DIP залишається domain-agnostic core.
- Dzvin.co не вбудовує DIP internal logic напряму.
- Explainability і audit artifacts є частиною core contract, а не optional UI add-on.

## Open Technical Risks
- Надмірна latency при розширенні explainability payloads.
- Складність backward compatibility при еволюції decision contract.
- Інтеграційний drift між DIP API та продуктними командами.

## Acceptance Criteria
- Архітектурні шари мають однозначні boundaries і responsibility map.
- Визначено mandatory artifacts для кожного decision execution.
- Є узгоджений шлях масштабування до multi-domain reuse.

## Links
- Related docs: 16-decision-engine.md, 17-feature-store.md, 18-model-registry.md, 24-experiment-tracking.md, 33-integration.md, 34-api.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
