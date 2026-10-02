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

and:

```text
E_QDIP^(d) <= 0.5 * E_specialized^(d)
```

The gate is evaluated separately for A, B and C. No cross-domain averaging is allowed for the primary claim.

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

## 6. Engineering-effort accounting

Primary observed engineering effort:

```text
E_d =
  E_model
+ E_implementation
+ E_test
+ E_integration
+ E_deployment
+ E_audit
```

Record actual person-hours and, where needed, direct external cost. Do not introduce post-hoc weights.

For each component record:

- contributor;
- role/competence level;
- task description;
- start/end or logged effort;
- artifact/commit/issue reference;
- whether effort is reusable Core work or domain-specific work.

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

## 8. Invalid experiment rules

A primary run is invalid if any of the following occurs without a pre-registered exception:

- Core/IR/API semantic change after freeze;
- baseline scope changed after viewing results;
- scenario or episode selection changed after viewing results;
- `S_d` or `epsilon_d` changed post hoc;
- unequal information is supplied to compared systems;
- compute budget materially differs without pre-registration;
- evaluation code changes after results are known;
- hidden domain-specific optimizer logic is added through a plugin;
- solver failure is silently removed rather than handled by the registered rule.

Invalid runs may be reported as exploratory evidence but cannot support the primary claim.

## 9. Test sequence

### Test A — Readiness Recovery

Purpose: validate methodology and produce first quantitative evidence.

### Test B — Procurement

Purpose: cross-domain transfer through the same runtime/IR.

### Test C — Blind independent domain

Purpose: primary generalization test after frozen Core/IR/API.

## 10. Realized outcomes and causal language

Report separately:

- model-implied expected utility;
- observed realized utility;
- reference-normalized regret/loss;
- benchmark difference.

Do not interpret observational realized difference as causal uplift unless the evaluation provides a credible counterfactual design (e.g. randomized assignment or another justified causal design).

## 11. Reproducibility

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
execution_timestamp
```

Evidence must be replayable from frozen artifacts or explain any unavoidable nondeterminism.
