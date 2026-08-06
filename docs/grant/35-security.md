# Security

## Document Metadata
- Owner: Security Lead
- Contributors: Platform Engineering, DevOps, Privacy Officer
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Описати security framework для DIP + Dzvin.co з фокусом на захист чутливих даних і цілісність decision pipelines.

## Security Objectives
- Confidentiality of sensitive user and organizational data.
- Integrity of decision workflows and policy states.
- Availability of core decision services.
- Traceability for incident response and audit.

## Threat Model Scope
- API misuse and credential leakage.
- Unauthorized cross-tenant data access.
- Data tampering in feature/decision artifacts.
- Supply chain and dependency risks.
- Insider misuse of diagnostics surfaces.

## Core Controls
- Strong authentication and scoped authorization.
- Tenant isolation at data and service layers.
- Encryption in transit and at rest.
- Immutable audit trails for sensitive operations.
- Secrets management and rotation policy.

## Application Security
- Input validation on all public decision endpoints.
- Rate limiting and abuse detection.
- Secure defaults for fallback paths.
- Least-privilege service permissions.

## Data Security
- Data classification and handling policy.
- Restricted access to individual-level records.
- Masking/anonymization for analytical views.
- Controlled export procedures.

## Operational Security
- Vulnerability scanning and patch SLAs.
- Dependency monitoring.
- Logging and anomaly alerting.
- Incident response runbooks.

## AI/Decision-Specific Security
- Protection against feature poisoning where feasible.
- Policy override governance and audit.
- Safeguards against prompt/data leakage in AI-assisted summaries.

## Incident Response
- Severity tiers and response times.
- Forensic logging requirements.
- Communication protocol for impacted stakeholders.

## Acceptance Criteria
- Security controls mapped to identified threats.
- Critical endpoints covered by authN/authZ + audit.
- Incident response drills and evidence documented.

## Links
- Related docs: 34-api.md, 36-gdpr.md, 37-ethics.md, 44-risk-management.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
