# 04 — Methodology

## 1. Design principle

The Universal Runtime thesis is evaluated by two independent criteria:

1. decision-quality non-inferiority;
2. engineering-effort reduction.

Neither criterion may compensate for failure of the other.

## 2. Domain-level primary gate

For each mandatory domain `d`:

```text
NR_QDIP^(d) <= NR_specialized^(d) + epsilon_d
```

and for domain-marginal engineering effort:

```text
E_domain,QDIP^(d) <= 0.5 * E_domain,specialized^(d)
```

The gate is evaluated separately for A, B and C. No cross-domain averaging is allowed for the primary claim.

The `50%` threshold is a pre-registered materiality threshold for the MVP/product thesis. It is not derived from optimization theory and must not be presented as a universal scientific constant.

## 3. Reference-normalized regret/loss

For a utility-maximization formulation:

```text
NR_d = (U_ref,d - U_d) / S_d
```

Requirements:

- `S_d` is fixed before primary runs;
- `S_d` is independent of all compared-system results;
- `S_d > 0` and has a domain interpretation;
- reference hierarchy is fixed before the experiment;
- the same reference and scale are used for QDIP and all baselines.

Reference hierarchy:

1. certified optimum;
2. certified mathematical bound where valid for the comparison;
3. pre-registered best-known feasible reference.

When the third case is used, report `reference-normalized regret/loss`; do not call it oracle regret.

## 4. Non-inferiority test

For each domain, define before execution:

- primary per-episode quality quantity;
- `epsilon_d`;
- aggregation rule;
- confidence level;
- paired/non-paired design;
- statistical test or interval procedure;
- handling of failed/infeasible solver runs;
- missing-data rule.

The primary statistical claim must test non-inferiority directly. A generic significance test of "no difference" is not sufficient.

If QDIP and the specialized implementation compile the same formal model to the same solver/backend, quality non-inferiority primarily demonstrates semantic preservation of the generic representation/runtime, not superiority of the optimizer. Claims must use that language.

## 5. Equal-scope comparison

The specialized baseline and QDIP implementation must target the same externally visible scope:

- same input information;
- same action space/problem definition;
- same hard constraints;
- same business objective/evaluation metric;
- same evaluation horizon;
- equivalent tests;
- equivalent deployment requirement;
- equivalent audit/reproducibility requirement;
- comparable compute budget where compute materially affects quality.

A simpler bespoke baseline cannot be used to manufacture an engineering advantage, and a richer QDIP implementation cannot receive additional information unavailable to the baseline.

The baseline team/implementation must have comparable competence for the relevant stack. Where possible, use independent or crossover review to reduce learning-effect bias.

## 6. Engineering-effort accounting

Two distinct engineering quantities must be reported.

### 6.1 Domain-marginal effort — primary product gate

```text
E_domain,d =
  E_model
+ E_implementation
+ E_test
+ E_integration
+ E_deployment
+ E_audit
```

This measures the incremental effort needed to add domain `d` once the reusable platform exists.

Primary engineering gate:

```text
E_domain,QDIP^(d) <= 0.5 * E_domain,specialized^(d)
```

### 6.2 Cumulative platform-adjusted effort — mandatory secondary economic metric

```text
E_cumulative,QDIP^(A..d) =
  E_core_IR_runtime
+ sum(E_domain,QDIP^(i), i=A..d)
```

Compare against:

```text
E_cumulative,specialized^(A..d) =
  sum(E_domain,specialized^(i), i=A..d)
```

This prevents the research narrative from hiding the up-front investment required to build Core/IR/runtime. The primary product thesis may focus on marginal domain cost, but the grant/business case must report the cumulative break-even trajectory.

Record actual person-hours and, where needed, direct external cost. Do not introduce post-hoc weights.

For each component record:

- contributor;
- role/competence level;
- task description;
- actual effort;
- artifact/commit/issue reference;
- reusable-Core vs domain-specific classification.

Projected maintenance surface is reported separately and is not part of the primary MVP gate.

## 7. Freeze protocol

Before primary Test A benchmark execution record:

- Core commit/hash;
- Canonical Decision IR schema/semantic version;
- extension API version;
- baseline code/version;
- solver versions/configuration;
- scenario dataset/version;
- evaluation seeds;
- `S_A`;
- `epsilon_A`;
- reference hierarchy;
- statistical procedure;
- invalidation rules.

Before blind Test C additionally freeze the extension surface. No new semantic construct may be introduced to pass Test C.

## 8. Blind Test C selection rule

The Test C domain must not be selected after inspecting which candidate domain best fits the frozen IR.

Before the Core/IR/API freeze, pre-register one of the following mechanisms:

1. a single named Test C domain fixed in advance;
2. a finite candidate set plus deterministic/random selection rule executed after freeze;
3. selection by an external validation partner/reviewer who has not optimized the choice around IR limitations.

The selected domain and selection evidence become part of the experiment manifest.

If Test C requires a new constraint/objective/risk/transition/solver semantic, generalization fails even when the new behavior can be hidden behind an extension/plugin without changing Core LOC.

## 9. Invalid experiment rules

A primary run is invalid if any of the following occurs without a pre-registered exception:

- Core/IR/API semantic change after freeze;
- baseline scope changed after viewing results;
- scenario or episode selection changed after viewing results;
- Test C domain selected opportunistically after inspecting IR fit;
- `S_d` or `epsilon_d` changed post hoc;
- unequal information is supplied to compared systems;
- compute budget materially differs without pre-registration;
- evaluation code changes after results are known;
- hidden domain-specific optimizer logic is added through a plugin;
- solver failure is silently removed rather than handled by the registered rule.

Invalid runs may be reported as exploratory evidence but cannot support the primary claim.

## 10. Test sequence

### Test A — Readiness Recovery

Purpose: validate methodology and produce first quantitative evidence.

### Test B — Procurement

Purpose: cross-domain transfer through the same runtime/IR.

### Test C — Blind independent domain

Purpose: primary generalization test after frozen Core/IR/API and pre-registered domain-selection mechanism.

## 11. Realized outcomes and causal language

Report separately:

- model-implied expected utility;
- observed realized utility;
- reference-normalized regret/loss;
- benchmark difference.

Do not interpret observational realized difference as causal uplift unless the evaluation provides a credible counterfactual design.

## 12. Reproducibility

Every primary run must have an experiment manifest containing at least:

```text
experiment_id
protocol_version
core_commit
ir_version
extension_api_version
baseline_version
solver_versions
scenario_version
seed
S_d
epsilon_d
reference_type
compute_budget
engineering_scope_version
test_c_selection_rule_version
execution_timestamp
```

Evidence must be replayable from frozen artifacts or explain any unavoidable nondeterminism.
