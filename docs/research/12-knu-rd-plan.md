# KNU R&D Collaboration Plan

Мова: Українська (default) | [English](12-knu-rd-plan.en.md)

## Document Metadata

- Owner: Scientific Coordinator
- Contributors: KNU Faculty Lead, ML Lead, Research Ops
- Version: 0.1
- Last Updated: 2026-08-08
- Status: Draft

## Purpose

Формалізувати науково-дослідну співпрацю з академічним партнером (Київський національний університет імені Тараса Шевченка, КНУ) у межах R&D-програми Dzvin.co + DIP.

## 1. Математична проблема

Поточна модель ризику використовує **фіксовані, вручну підібрані ваги та пороги**:

- ваги state risk (0.34/0.22/0.18/0.16/0.10);
- коефіцієнти EWMA (α=0.38, decay ρ=0.92);
- пороги рішень (0.38 / 0.68 для risk levels; 0.45 / 0.65 для trust).

Формальна постановка:

$$\hat{\mathbf{w}}, \hat{\theta} = \arg\min_{\mathbf{w}, \theta} \; \mathbb{E}_{(\mathbf{x}, y)}\left[ \mathcal{L}(f_{\mathbf{w},\theta}(\mathbf{x}), y) \right] \quad \text{s.t.} \quad \sum w_i = 1,\; w_i \geq 0$$

де $\mathcal{L}$ — calibration-aware loss, $f$ — hybrid decision function, $y$ — outcome (worsened / not_worsened).

## 2. Існуючий підхід та його недоліки

**Існуючий підхід:** евристична композиція сигналів із ручним налаштуванням.

**Недоліки:**

- відсутність теоретичних гарантій оптимальності ваг;
- фіксовані пороги не адаптуються до розподілу популяції;
- немає формальної моделі невизначеності для feasible state space;
- minimax bounds побудовані на консервативних апроксимаціях, а не на статистично обґрунтованих інтервалах.

## 3. Запропонована нова модель

Замінити ручні евристики на data-driven формалізм:

- **Оптимізація ваг:** constrained optimization (Bayesian / projected gradient) на outcome data.
- **Персоналізовані пороги:** per-cohort calibration з ізотонічною регресією.
- **Формальні credible intervals:** bootstrap-based замість fixed margins.
- **Minimax → decision theory:** формальне відображення worst-case bounds на intervention policy.

## 4. Що досліджує кафедра (розподіл робіт)

| Напрям                         | Відповідальний             | Внесок КНУ                                       |
| ------------------------------ | -------------------------- | ------------------------------------------------ |
| Оптимізація ваг та порогів     | Кафедра / ML Lead          | Теоретичне обґрунтування convergence, вибір loss |
| Uncertainty quantification     | Кафедра статистики         | Bootstrap CI, calibration theory                 |
| Minimax decision formalization | Кафедра / Decision Science | Robust optimization, decision-theoretic bounds   |
| Time-series stability          | Кафедра / ML               | Drift theory, stationarity tests                 |
| Statistical validation         | Кафедра статистики         | Hypothesis testing design, power analysis        |

> Конкретні назви кафедр та ПІБ керівників — заповнити після підписання угоди про співпрацю.

## 5. Експерименти

| ID              | Дослідницьке питання                          | Метод                            | Owner                 |
| --------------- | --------------------------------------------- | -------------------------------- | --------------------- |
| EXP-AB-001      | Чи покращує персональний baseline калібрацію? | Segment comparison, bootstrap CI | ML Lead + КНУ         |
| EXP-HYB-002     | Hybrid vs pure ML vs rules-only               | Offline ablation                 | ML Lead               |
| EXP-004         | Стабільність adaptive features під drift      | Drift simulation                 | КНУ (drift theory)    |
| EXP-WEIGHT-006  | Оптимальні ваги проти ручних                  | Constrained optimization         | КНУ + ML Lead         |
| EXP-MINIMAX-007 | Minimax vs point estimate                     | Interval coverage analysis       | КНУ (decision theory) |

## 6. Критерії успішності

- Calibration error < 0.15 після оптимізації ваг (зараз не вимірюється систематично).
- AUROC оптимізованої моделі ≥ baseline + preregistered margin, з 95% CI.
- Minimax interval coverage ≥ 90% на held-out даних.
- Статистична значущість покращень (p < 0.05, з корекцією на множинні порівняння).

## 7. Очікувані наукові результати

- Спільна публікація: "Adaptive risk modeling for corporate mental wellbeing" (target: peer-reviewed journal / conference).
- Preprint з формальним описом hybrid decision governance.
- Відкрита специфікація алгоритму state-vector risk assessment.
- Дипломні / магістерські роботи студентів КНУ на основі проєктних даних (за етичним погодженням).

## 8. Модель співпраці

- Юридична основа: угода про науково-технічну співпрацю між компанією та КНУ.
- IP: спільні наукові результати публікуються; production policies залишаються proprietary (див. `docs/research/07-ip-strategy.md`).
- Дані: доступ студентів/дослідників лише до pseudonymized / aggregated наборів (див. `docs/research/09-data-management-plan-dmp.md`).
- Каденція: щомісячні наукові рев'ю, щоквартальні milestone-звіти.

## Links

- Related docs: 02-scientific-hypotheses.md, 11-rd-technical-dossier.md, experiment-registry.md, 07-ip-strategy.md

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
