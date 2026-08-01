# Risk Register

## Purpose
Живий реєстр ризиків для щомісячного оновлення (не narrative документ).

| Risk ID | Category | Description | Probability | Impact | Mitigation | Owner | Status | Review Date |
|---------|----------|-------------|-------------|--------|------------|-------|--------|-------------|
| R-001 | Scientific | Гіпотези не дають статистично значущого ефекту. | Medium | High | Перегляд експериментального дизайну, power recalculation. | Scientific Lead | Open | 2026-09-01 |
| R-002 | Data Quality | Недостатнє покриття/повнота даних для ключових features. | Medium | High | Quality gates, missingness diagnostics, fallback policy. | Data Lead | Open | 2026-09-01 |
| R-003 | Technical | Деградація latency в online decision flows. | Medium | Medium | Profiling, caching, SLO alerts, performance budget. | Platform Lead | Open | 2026-09-01 |
| R-004 | Compliance | GDPR non-conformant data handling in pilot operations. | Low | High | DPIA, SOP enforcement, access audits. | DPO | Open | 2026-09-01 |
| R-005 | Adoption | Низьке прийняття рекомендацій у B2B користувачів. | Medium | Medium | UX iterations, explainability tuning, onboarding playbook. | Product Lead | Open | 2026-09-01 |
| R-006 | Model Governance | Drift causes unstable policy decisions. | Medium | High | Trust gating, auto-mitigation, rollback triggers. | ML Lead | Open | 2026-09-01 |
