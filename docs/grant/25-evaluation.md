# Evaluation Protocol

Мова: Українська (default) | [English](25-evaluation.en.md)

## Document Metadata

- Owner: Evaluation Lead
- Contributors: Data Science, Product Analytics, Scientific Coordinator
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose

Визначити єдиний протокол оцінювання для rule/ML/hybrid рішень та їх впливу на практичні outcomes.

## Evaluation Questions

- Чи покращує hybrid engine якість рішень проти baselines?
- Чи зберігається якість у різних сегментах?
- Чи explainability підвищує довіру і прийняття рішень?

## Baselines

- Deterministic rules baseline.
- Heuristic scoring baseline.
- Current production policy baseline.

## Evaluation Layers

- Predictive layer: discrimination, calibration, uncertainty quality.
- Decision layer: action relevance and disagreement handling.
- Product layer: adoption, trust, time-to-action.

## Core Metrics (summary)

- AUROC / AUPRC
- Calibration error
- Precision@high-risk
- False alert rate
- Trust score uplift
- Policy stability index

## Segment Analysis

- By company size
- By team type
- By engagement strata
- By data completeness strata

## Acceptance Threshold Policy

- Primary metrics must beat baseline with predefined margin.
- No critical degradation in protected or sensitive cohorts.
- Confidence intervals must exclude harmful regression region.

## Online Evaluation Rules

- Minimal sample before decisive policy updates.
- Guardrails for rollback.
- Auto-mitigation on degraded cycles.

## Backtesting on Historical Data

- Time-based split: training на даних < cutoff, testing на даних ≥ cutoff (no leakage).
- Rolling-origin backtest: послідовне зміщення cutoff для оцінки стабільності в часі.
- Replay historical risk events через поточну policy для порівняння з фактичними outcomes.
- Метрики backtest: AUROC/AUPRC по періодах, calibration drift, alert precision у часі.

## Generalizability Checks

- Cross-cohort validation: навчання на одних компаніях/командах, тест на інших.
- Segment robustness: перевірка стабільності метрик по company size, team type, engagement strata.
- Out-of-distribution probe: оцінка деградації на когортах з нетиповим baseline.
- Критерій: відсутність critical degradation у жодному захищеному сегменті.

## Reporting Format

- Executive summary (non-technical)
- Technical appendix with metric definitions
- Risk and bias section
- Reproducibility references

## Decision Gates

- Gate A: research readiness
- Gate B: limited rollout
- Gate C: production default policy

## Acceptance Criteria

- Протокол покриває offline + online етапи.
- Визначені stop conditions і rollback criteria.
- Є шаблон reviewer-ready evaluation report.

## Links

- Related docs: 12-statistics.md, 26-metrics.md, 27-clinical-validation.md, 29-explainability-validation.md

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
