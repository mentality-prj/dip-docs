# Uncertainty Estimation

Language: [Українська (default)](22-uncertainty.md) | English

## Document Metadata
- Owner: ML Lead
- Contributors: Decision Science, Responsible AI Lead
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Визначити, як оцінювати та використовувати невизначеність у рішенні, щоб зменшити ризик хибних дій.

## Uncertainty Types
- Data uncertainty: sparse/noisy/missing inputs.
- Model uncertainty: unstable prediction under perturbations.
- Policy uncertainty: conflicting decision signals.

## Estimation Signals
- Confidence score from input completeness.
- Stability under bootstrap/perturbation checks.
- Disagreement indicators between rule and ML outputs.
- Cohort coverage adequacy markers.

## Decision Policy Integration
- High risk + high uncertainty -> human review path.
- Low uncertainty + consistent signals -> standard action path.
- Persistent uncertainty -> additional data request/observation period.

## Communication Layer
- Role-adapted uncertainty explanation.
- Clear distinction: "low confidence" != "no risk".
- Avoid deterministic language under uncertainty.

## Monitoring
- Distribution of confidence levels over time.
- Correlation between uncertainty and downstream errors.
- Uncertainty drift alerts.

## Acceptance Criteria
- Кожен decision output містить uncertainty marker.
- Є policy rules для uncertainty-triggered safeguards.
- Uncertainty quality входить у регулярний evaluation цикл.

## Links
- Related docs: 20-explainability.md, 21-adaptive-baseline.md, 25-evaluation.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
