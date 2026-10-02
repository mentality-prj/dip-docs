# 01 — Executive Summary

## Project

QDIP Universal Decision Runtime is a lightweight execution layer for structured operational decisions under uncertainty.

It is designed to accept a declarative decision specification containing state, actions, constraints, uncertainty, utility/risk semantics and horizon, compile it into a canonical optimization representation, execute it through a generic solver boundary, and produce an auditable decision result with replay and realized-outcome evaluation.

## Problem

Operational decision systems are frequently implemented as bespoke pipelines. Even when mature optimization libraries or enterprise platforms are available, substantial engineering is still required to translate each domain into a production decision model, integrate data and constraints, implement evaluation, and provide auditability.

The project does not claim that QDIP invents a superior mathematical optimizer. The research question is whether a reusable domain-agnostic runtime can preserve decision quality relative to specialized implementations while substantially reducing engineering effort.

## Central empirical claim

For every reference domain `d`:

```text
NR_QDIP^(d) <= NR_specialized^(d) + epsilon_d
E_QDIP^(d) <= 0.5 * E_specialized^(d)
```

`NR` is a pre-registered reference-normalized regret/loss measure. `E` is observed engineering effort across the same lifecycle scope.

The decision-quality and engineering-reduction criteria are tested separately.

## Validation domains

- Test A: Readiness Recovery.
- Test B: Procurement Decision.
- Test C: blind independent operational domain after Core/IR/API freeze.

Test C is the main generalization test. If a new constraint type, objective semantic, transition semantic or solver semantic must be added after the freeze, the generalization claim fails for that test.

## Product advantage being tested

QDIP is intended to occupy the layer between data/enterprise systems and execution systems:

```text
ERP / BI / APIs / domain data
            ↓
       DecisionSpec
            ↓
   Canonical Decision IR
            ↓
       QDIP Runtime
            ↓
 recommendation / policy / Pareto set
            ↓
 execution system + realized outcome
```

The target advantage is not dashboard breadth or solver novelty. It is reusable decision engineering: comparable decision quality with materially lower implementation, integration and deployment effort.

## Grant purpose

Grant-funded work should therefore focus on:

1. formal decision semantics and Canonical Decision IR;
2. reproducible pre-registered benchmark methodology;
3. validation in heterogeneous operational domains;
4. blind transfer after freeze;
5. quantitative engineering-cost evidence;
6. external operational validation;
7. TRL progression toward production deployment.

## Expected evidence

By submission/final project stage the evidence package should contain:

- frozen Core/IR/API identifiers;
- Test A quantitative report;
- Test B quantitative report;
- blind Test C generalization report;
- engineering-effort comparison against equal-scope specialized baselines;
- reproducibility artifacts and audit traces;
- at least one external validation partner / LOI;
- IP/FTO, exploitation, budget and TRL documentation.
