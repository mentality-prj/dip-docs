# 06 — Test A Pre-registration Protocol: Readiness Recovery

Status: draft for pre-registration. Do not run primary benchmark until all `TBD` fields are resolved and the protocol is frozen.

## 1. Purpose

Test A provides the first quantitative evidence for the QDIP Universal Runtime thesis using the Readiness Recovery use case currently represented in Observatory.

Primary goals:

1. test decision-quality non-inferiority versus an equal-scope specialized operational optimizer;
2. test at least 50% reduction in domain-marginal observed engineering effort;
3. report cumulative platform-adjusted effort separately;
4. validate the benchmark/evidence pipeline before Test B and blind Test C.

## 2. Decision problem

Given:

- current fleet/asset state;
- required capability/readiness target;
- candidate recovery actions;
- costs;
- durations;
- resource/skill/part constraints;
- dependencies;
- uncertainty in action completion/effect;
- deadline/horizon;

produce a feasible recovery plan or Pareto set that trades off readiness, cost, time and risk according to the frozen utility/risk semantics.

## 3. Compared systems

### QDIP

Readiness Recovery expressed through DecisionSpec → Canonical Decision IR → QDIP Runtime.

### Baseline B1 — Operational heuristic

A strong documented rule/heuristic representative of realistic operational planning, not a deliberately weak comparator.

Exact definition: `TBD before freeze`.

### Baseline B2 — Specialized optimizer

Equal-scope bespoke/specialized implementation of the same formal problem using a suitable optimization stack.

Exact implementation/backend: `TBD before freeze`.

The specialized baseline must not be intentionally under-engineered and must satisfy the same test/deployment/audit requirements used in engineering-effort accounting.

## 4. Equal-information rule

All compared systems receive the same:

- initial state;
- candidate actions/variables;
- hard constraints;
- uncertainty inputs/scenarios;
- horizon;
- objective/evaluation semantics;
- information available at each decision time;
- evaluation worlds.

No system may access realized outcomes before making the evaluated decision.

## 5. Primary decision-quality metric

Use reference-normalized regret/loss.

For utility-maximization form:

```text
NR_A = (U_ref,A - U_A) / S_A
```

Pre-registration fields:

- `U_ref,A` reference type/value rule: `TBD`;
- `S_A`: `TBD`;
- rationale for `S_A`: `TBD`;
- `epsilon_A`: `TBD`;
- aggregation/statistical procedure: `TBD`;
- confidence level: `TBD`.

Primary non-inferiority gate:

```text
NR_QDIP^(A) <= NR_specialized^(A) + epsilon_A
```

The statistical procedure must test non-inferiority directly.

If both implementations encode the same formal model and use the same solver/backend, a successful result is evidence of semantic preservation through the QDIP abstraction, not optimizer superiority.

## 6. Secondary operational metrics

Report but do not substitute for the primary gate:

- readiness at deadline;
- total recovery cost;
- time-to-recovery;
- probability of readiness/capability shortfall;
- CVaR / expected shortfall where defined;
- hard-constraint violations;
- solver feasibility rate;
- compute time/cost;
- Pareto-front characteristics where applicable.

## 7. Evaluation worlds

Primary scenarios/worlds must be fixed before viewing primary results.

Required manifest fields:

```text
scenario_set_version
number_of_worlds
seed_list
uncertainty_generation_method
stress_scenarios
OOD_scenarios_if_primary
```

Current values: `TBD before freeze`.

Exploratory stress tests may be added after freeze only if explicitly labeled exploratory and excluded from primary evidence.

## 8. Engineering-effort evaluation

### 8.1 Primary domain-marginal gate

Observed domain effort:

```text
E_domain,A =
  E_model
+ E_implementation
+ E_test
+ E_integration
+ E_deployment
+ E_audit
```

Primary engineering gate:

```text
E_domain,QDIP^(A) <= 0.5 * E_domain,specialized^(A)
```

The `50%` threshold is a pre-registered MVP materiality threshold.

### 8.2 Mandatory cumulative metric

Historical/reusable Core, Canonical IR and runtime engineering is not counted as domain-marginal Test A effort, but it must not disappear from the economic evidence.

Report separately:

```text
E_cumulative,QDIP^(A) = E_core_IR_runtime + E_domain,QDIP^(A)
E_cumulative,specialized^(A) = E_domain,specialized^(A)
```

For later domains extend the cumulative comparison across A+B+C to estimate the break-even point of the reusable runtime.

This prevents a false claim that QDIP is already cheaper in total merely because its platform investment was incurred earlier.

### 8.3 Effort ledger rules

For every logged item record:

- person/role;
- competence level;
- activity category;
- actual hours;
- artifact/commit/issue reference;
- reusable-Core vs domain-specific classification.

The specialized baseline must be implemented/evaluated at equivalent quality, test, deployment, reproducibility and audit scope. Contributor competence should be comparable; major asymmetry must be disclosed.

Domain-specific QDIP work cannot be excluded merely because it is implemented as a plugin or adapter.

## 9. Scope-equivalence checklist

Before freeze, both QDIP and specialized implementation must satisfy the same required scope:

- same input contract;
- same constraint semantics;
- same utility/evaluation semantics;
- same uncertainty data;
- same reproducibility requirement;
- same automated-test target;
- same deployment target;
- same audit/evidence target;
- comparable contributor competence assumptions.

Any justified difference must be pre-registered.

## 10. Freeze point

Primary Test A starts only after recording:

```text
protocol_version
qdip_core_commit
canonical_ir_version
canonical_ir_semantic_hash
extension_api_version
qdip_solver_adapter_version
specialized_baseline_commit
solver_versions_and_configs
scenario_set_version
seed_list
S_A
epsilon_A
reference_rule
statistical_test
compute_budget_rule
engineering_scope_version
```

## 11. Invalid experiment criteria

Primary evidence is invalid if, after freeze and before unblinding/completion, any of the following occurs outside a pre-registered exception:

- QDIP Core semantic change;
- Canonical IR semantic change;
- extension API semantic change;
- baseline scope/algorithm changed after observing comparative results;
- scenario selection changed after observing results;
- `S_A` or `epsilon_A` changed;
- unequal information supplied;
- evaluation metric changed;
- compute budget unfairly changed;
- engineering-scope rules changed after observing effort/result comparisons;
- failed episodes selectively removed;
- domain-specific bespoke optimization is hidden inside a QDIP plugin.

Invalid runs may be retained as exploratory evidence but must not support the primary claim.

## 12. Test A pass condition

Test A passes only if both independent primary criteria pass:

```text
Decision quality:
NR_QDIP^(A) <= NR_specialized^(A) + epsilon_A

Domain-marginal engineering:
E_domain,QDIP^(A) <= 0.5 * E_domain,specialized^(A)
```

The cumulative platform-adjusted effort is reported separately and cannot be omitted from product/grant economics.

A pass on one primary criterion cannot compensate for failure of the other.

## 13. Test A evidence output

After execution create `07-test-a-results.md` containing:

- frozen manifest;
- all primary results;
- confidence intervals/non-inferiority result;
- operational metrics;
- domain-marginal engineering ledger summary;
- cumulative platform-adjusted effort;
- invalid/failed runs;
- deviations from protocol;
- conclusion limited to the pre-registered claim.
