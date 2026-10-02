# 05 — Architecture + Canonical Decision IR

## 1. Architectural thesis

QDIP is a reusable decision runtime, not a collection of domain-specific optimizers.

The required boundary is:

```text
Domain data / adapter
        ↓
    DecisionSpec
        ↓
Canonical Decision IR
        ↓
   QDIP Runtime
   ├─ validation
   ├─ uncertainty/risk
   ├─ solver selection/adapters
   ├─ replay/evaluation
   └─ audit
        ↓
   DecisionResult
```

The Canonical Decision IR is the main architectural evidence for the Universal Runtime thesis.

## 2. DecisionSpec vs Canonical Decision IR

### DecisionSpec

Human/domain-facing declarative contract. It may use domain names and identifiers.

Example concerns:

- assets;
- suppliers;
- repair actions;
- procurement dates;
- budgets;
- deadlines.

### Canonical Decision IR

Domain-agnostic executable semantics produced by compiling/normalizing DecisionSpec.

The solver layer receives IR, not raw domain objects.

## 3. Minimum IR concepts

The initial frozen IR should explicitly represent:

- typed parameters/state inputs;
- decision variables;
- domains/bounds;
- hard constraints;
- soft constraints/penalties;
- objective terms;
- multiple objectives / Pareto metadata where applicable;
- uncertainty/scenario inputs;
- risk measures;
- time/horizon indices;
- outcome/evaluation expressions;
- solver capability requirements;
- provenance and semantic version metadata.

If sequential problems are in MVP scope, the freeze must also define:

- state transition semantics;
- observation semantics;
- policy/replanning boundary;
- decision epochs.

If these are not frozen before Test C, sequential transfer cannot be claimed by Test C.

## 4. Constraint compilation

The runtime must not enumerate and filter the entire action space as a generic architecture assumption.

For combinatorial problems the adapter/compiler must translate the declarative problem into symbolic IR constraints and decision variables that are passed to solver adapters.

This supports action spaces that cannot be explicitly enumerated.

## 5. Solver boundary

Correct abstraction:

```text
Domain → DecisionSpec → Canonical IR → Solver Adapter → Solver
```

A solver adapter may translate canonical IR constructs into Pyomo, OR-Tools/CP-SAT, MILP solver APIs or another supported backend.

A solver adapter must not contain domain semantics.

## 6. Extension surface

Before blind Test C, pre-register and freeze all allowed extension categories.

Permitted examples:

- data-type adapters;
- value encoders/decoders;
- solver backend adapters implementing already-frozen IR semantics;
- domain data transformations into DecisionSpec;
- pure functions explicitly permitted by the frozen expression/function contract.

Not permitted after freeze:

- a new kind of constraint semantic;
- a new objective/utility semantic;
- a new risk semantic needed only for Test C;
- a new transition/observation semantic;
- domain-specific search/optimization loop;
- a plugin that bypasses IR and directly solves the domain problem.

Any such requirement is a Core/IR generalization failure.

## 7. Versioning and freeze artifacts

Freeze artifact should include:

```text
core_commit
ir_schema_version
ir_semantic_version
extension_api_version
solver_adapter_versions
schema_hash
semantic_spec_hash
```

JSON/YAML schema stability alone is insufficient. Semantic meaning must also be versioned.

## 8. Validation requirements

IR validation should distinguish:

- structural/schema validation;
- semantic validation;
- capability validation against selected solver backend;
- dimensional/unit consistency where supported;
- infeasibility detected by the solver rather than assumed through enumeration.

## 9. Evidence for generalization

For each domain report:

- DecisionSpec size;
- generated IR size;
- domain-specific executable LOC;
- adapter LOC;
- custom extension count;
- unsupported semantic constructs encountered;
- Core/IR/API changes;
- solver adapter used.

Test C passes the architecture portion only if no new semantic construct is required after freeze.
