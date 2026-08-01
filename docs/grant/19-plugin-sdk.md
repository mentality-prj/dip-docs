# Plugin SDK

## Document Metadata
- Owner: Platform Architect
- Contributors: Core Backend Team, Developer Experience Lead
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити SDK-підхід для розширення DIP без модифікації core, із безпечним життєвим циклом плагінів.

## Plugin Categories
- Rule plugins
- Feature extractor plugins
- Model inference plugins
- Explainability provider plugins
- Connector/source plugins

## SDK Contract Principles
- Stable interfaces with versioning.
- Explicit capability declarations.
- Resource and permission boundaries.
- Deterministic error contracts.

## Plugin Manifest (Draft)
- plugin_id
- version
- capabilities
- required_permissions
- compatible_sdk_versions
- healthcheck endpoint/hook

## Runtime Controls
- Sandboxed execution where possible.
- Timeout and resource limits.
- Fallback behavior on plugin failure.
- Observability hooks for plugin metrics.

## Security Review
- Static and dependency scanning.
- Permission review.
- Secrets handling constraints.

## Certification Path
- Dev/test certification
- Staging validation
- Production approval

## Acceptance Criteria
- Core не потребує змін для стандартних plugin extensions.
- Кожен plugin має manifest, tests, and observability hooks.
- Є documented deprecation path для SDK changes.

## Links
- Related docs: 15-dip-architecture.md, 16-decision-engine.md, 35-security.md
