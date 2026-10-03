# 08 — Test B Procurement Protocol

Status: **PROTOCOL DRAFT — FREEZE BEFORE PRIMARY EXECUTION**

## Objective

Test B evaluates whether the frozen QDIP Core and Canonical Decision IR can represent and execute a procurement decision problem without bespoke domain logic leaking into Core, while preserving decision quality relative to an equally scoped specialized implementation and materially reducing domain-marginal engineering effort.

Primary gates:

```text
NR_QDIP^(B) <= NR_specialized^(B) + epsilon_B
E_domain,QDIP^(B) <= 0.5 * E_domain,specialized^(B)
```

## Decision family

The benchmark should use a bounded operational procurement problem with:

- explicit purchase/commitment actions;
- known obligations or demand;
- timing/deadline semantics;
- prices/costs available at decision time;
- uncertainty represented only from information available before the decision;
- hard budget/capacity/contract constraints where applicable;
- realized procurement cost or realized utility as the outcome.

The benchmark must not depend on a claim that QDIP predicts markets better than a dedicated forecasting system. QDIP is evaluated as a decision runtime.

## Equal-scope comparison

QDIP and the specialized baseline receive the same:

- decision-time data;
- preprocessing and feature definitions;
- action set;
- constraints;
- objective/utility definition;
- evaluation episodes;
- reference hierarchy;
- compute budget where relevant;
- operational failure rules.

The specialized baseline must be a credible implementation of the same decision problem, not a deliberately weak strawman.

## Pre-freeze items

Freeze before primary evaluation:

1. procurement scenario family and episode construction;
2. baseline identity/implementation;
3. reference hierarchy;
4. `S_B` and `epsilon_B`;
5. evaluation horizon and data snapshot/checksums;
6. seeds and statistical procedure;
7. missing-data/fallback semantics;
8. compute/information budgets;
9. engineering-effort accounting rules;
10. Core/IR/API immutable reference.

## Primary metrics

- reference-normalized procurement loss/regret;
- realized all-in cost or realized utility, where supported by the benchmark;
- hard-constraint violations;
- fallback/invalid-decision rate;
- decision latency where operationally material;
- domain-marginal engineering effort by frozen category.

## Relationship to GF2

Existing gas-procurement research may provide source material, evidence discipline, provenance patterns and comparator design. It must not be silently reused as Test B primary evidence unless the Test B preregistration explicitly binds the same frozen problem, information set, baseline and data protocol.

## Completion condition

Test B is complete only when the preregistration, immutable execution identity, primary results, attempt ledger and engineering ledger are all archived and independently reproducible.