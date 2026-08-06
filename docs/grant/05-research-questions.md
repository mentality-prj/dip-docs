# Research Questions

Мова: Українська (default) | [English](05-research-questions.en.md)

## Document Metadata
- Owner: Scientific Coordinator
- Contributors: ML Lead, Product Research, Clinical Advisor
- Version: 0.2
- Last Updated: 2026-08-01
- Status: Draft

## Purpose
Задати ключові RQ та гіпотези, які визначають план експериментів і критерії успіху проєкту.

## RQ1: Personalization Effect
Чи підвищує персоналізований adaptive baseline якість прогнозу і рішень порівняно з non-personalized baseline?
- H1: Adaptive baseline покращує calibration і precision у high-risk сегменті.
- Primary metrics: calibration error, precision@high-risk, segment stability.

## RQ2: Hybrid vs Single-Paradigm
Чи hybrid rule+ML engine працює краще за rules-only і ML-only підходи?
- H2: Hybrid з policy governance дає кращий баланс accuracy/safety.
- Primary metrics: AUROC/AUPRC, false alert rate, disagreement resolution quality.

## RQ3: Explainability Impact
Чи role-aware explainability підвищує довіру і прийняття рішень?
- H3: Пояснення збільшують trust score і action adoption.
- Primary metrics: trust uplift, action acceptance, comprehension scores.

## RQ4: Governance Robustness
Чи online policy evaluation з auto-mitigation зменшує ризик деградації у production?
- H4: Trust-gated governance скорочує періоди degraded performance.
- Primary metrics: degradation duration, rollback frequency, safe-mode outcomes.

## RQ5: Transferability Potential
Наскільки архітектурний патерн DIP переносимий у суміжні домени?
- H5: Platform core reuse можливий з мінімальними змінами adapter layer.
- Primary metrics: integration effort, contract reuse ratio, time-to-first-value.

## Prioritization
- Primary RQ: RQ1-RQ3
- Secondary RQ: RQ4-RQ5

## Decision Rules
- Кожна H приймається/відхиляється за preregistered thresholds.
- Невизначені результати маркуються як inconclusive, не positive.

## Acceptance Criteria
- Для кожного RQ визначено метрики, тести, і stop criteria.
- RQ покривають excellence + impact + implementation dimensions.
- Є linkage до WP та evaluation protocol.

## Links
- Related docs: 06-methodology.md, 07-experimental-design.md, 12-statistics.md, 25-evaluation.md

## Horizon Europe References
- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
