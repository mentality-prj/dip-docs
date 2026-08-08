# KNU R&D Collaboration Plan

Language: [Українська (default)](12-knu-rd-plan.md) | English

## Document Metadata

- Owner: Scientific Coordinator
- Contributors: KNU Faculty Lead, ML Lead, Research Ops
- Version: 0.1
- Last Updated: 2026-08-08
- Status: Draft

## Purpose

Formalise the research collaboration with the academic partner (Taras Shevchenko National University of Kyiv, KNU) within the Dzvin.co + DIP R&D programme.

## 1. Mathematical Problem

The current risk model uses **fixed, manually tuned weights and thresholds**:

- state risk weights (0.34/0.22/0.18/0.16/0.10);
- EWMA coefficients (α=0.38, decay ρ=0.92);
- decision thresholds (0.38 / 0.68 for risk levels; 0.45 / 0.65 for trust).

Formal statement:

$$\hat{\mathbf{w}}, \hat{\theta} = \arg\min_{\mathbf{w}, \theta} \; \mathbb{E}_{(\mathbf{x}, y)}\left[ \mathcal{L}(f_{\mathbf{w},\theta}(\mathbf{x}), y) \right] \quad \text{s.t.} \quad \sum w_i = 1,\; w_i \geq 0$$

where $\mathcal{L}$ is a calibration-aware loss, $f$ is the hybrid decision function, and $y$ is the outcome (worsened / not_worsened).

## 2. Existing Approach and Its Weaknesses

**Existing approach:** heuristic composition of signals with manual tuning.

**Weaknesses:**

- no theoretical guarantee of weight optimality;
- fixed thresholds do not adapt to the population distribution;
- no formal uncertainty model for the feasible state space;
- minimax bounds rely on conservative approximations rather than statistically grounded intervals.

## 3. Proposed New Model

Replace manual heuristics with a data-driven formalism:

- **Weight optimisation:** constrained optimization (Bayesian / projected gradient) on outcome data.
- **Personalised thresholds:** per-cohort calibration with isotonic regression.
- **Formal credible intervals:** bootstrap-based instead of fixed margins.
- **Minimax → decision theory:** formal mapping of worst-case bounds to intervention policy.

## 4. Faculty Research Scope (Work Distribution)

| Direction                         | Responsible                | KNU Contribution                               |
| --------------------------------- | -------------------------- | ---------------------------------------------- |
| Weight and threshold optimisation | Faculty / ML Lead          | Convergence theory, loss selection             |
| Uncertainty quantification        | Statistics faculty         | Bootstrap CI, calibration theory               |
| Minimax decision formalisation    | Faculty / Decision Science | Robust optimization, decision-theoretic bounds |
| Time-series stability             | Faculty / ML               | Drift theory, stationarity tests               |
| Statistical validation            | Statistics faculty         | Hypothesis testing design, power analysis      |

> Specific department names and supervisor names — to be filled after the collaboration agreement is signed.

## 5. Experiments

| ID              | Research Question                             | Method                           | Owner                 |
| --------------- | --------------------------------------------- | -------------------------------- | --------------------- |
| EXP-AB-001      | Does a personal baseline improve calibration? | Segment comparison, bootstrap CI | ML Lead + KNU         |
| EXP-HYB-002     | Hybrid vs pure ML vs rules-only               | Offline ablation                 | ML Lead               |
| EXP-004         | Stability of adaptive features under drift    | Drift simulation                 | KNU (drift theory)    |
| EXP-WEIGHT-006  | Optimised weights vs manual                   | Constrained optimization         | KNU + ML Lead         |
| EXP-MINIMAX-007 | Minimax vs point estimate                     | Interval coverage analysis       | KNU (decision theory) |

## 6. Success Criteria

- Calibration error < 0.15 after weight optimisation (currently not measured systematically).
- AUROC of the optimised model ≥ baseline + preregistered margin, with 95% CI.
- Minimax interval coverage ≥ 90% on held-out data.
- Statistical significance of improvements (p < 0.05, with multiple-comparison correction).

## 7. Expected Scientific Results

- Joint publication: "Adaptive risk modeling for corporate mental wellbeing" (target: peer-reviewed journal / conference).
- Preprint with a formal description of hybrid decision governance.
- Open specification of the state-vector risk assessment algorithm.
- KNU student theses (bachelor / master) based on project data (subject to ethics approval).

## 8. Collaboration Model

- Legal basis: research-and-technical collaboration agreement between the company and KNU.
- IP: joint scientific results are published; production policies remain proprietary (see `docs/research/07-ip-strategy.md`).
- Data: student/researcher access limited to pseudonymized / aggregated datasets (see `docs/research/09-data-management-plan-dmp.md`).
- Cadence: monthly research reviews, quarterly milestone reports.

## Links

- Related docs: 02-scientific-hypotheses.md, 11-rd-technical-dossier.md, experiment-registry.md, 07-ip-strategy.md

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
