# 09 — Blind Test C Generalization Protocol

Status: **PROTOCOL DRAFT — MUST BE FROZEN BEFORE DOMAIN REVEAL**

## Purpose

Test C is the principal falsification test for the Universal Decision Runtime claim. It asks whether a Core/IR/API frozen before domain reveal can handle an independent operational domain without introducing new hidden decision semantics or a bespoke optimizer inside an extension.

Primary gates:

```text
NR_QDIP^(C) <= NR_specialized^(C) + epsilon_C
E_domain,QDIP^(C) <= 0.5 * E_domain,specialized^(C)
```

## Blindness boundary

Before the Test C domain is revealed, freeze:

- QDIP Core;
- Canonical Decision IR schema and semantics;
- extension API;
- allowed generic solver-adapter interfaces;
- engineering-effort taxonomy;
- domain-selection mechanism;
- benchmark-construction procedure;
- invalidation rules.

The implementation team must not tune Core/IR/API against the selected domain before the freeze.

## Domain-selection mechanism

The candidate registry must be defined before freeze and may contain operational families such as fleet allocation, inventory/replenishment, workforce/resource scheduling or another structured decision domain not used to design Core.

The selection method must be pre-registered and independent of which domain appears easiest for QDIP. Once selected, the domain cannot be swapped because results are inconvenient.

Any domain developed in a grant-specific overlay before Test C freeze — for example an agriculture adapter created for NOSTRADAMUS — must be excluded from the blind candidate pool.

## Generalization-failure rule

Test C fails the architectural generalization criterion if success requires any of the following after reveal:

- a new Core decision semantic;
- a new Canonical IR primitive that was not available at freeze;
- a domain-specific optimization algorithm hidden in a plugin;
- a domain-only constraint/objective/transition semantic that bypasses the extension contract;
- result-driven changes to `S_C`, `epsilon_C`, baseline scope, scenarios or reference rules.

A generic bug fix discovered after reveal requires a new versioned qualification chain; it cannot rewrite the original evidence.

## Evidence to archive

- frozen pre-reveal manifest;
- domain-selection proof;
- reveal timestamp and selected-domain identity;
- specialized baseline definition;
- scenario/data snapshot hashes;
- implementation diffs after reveal;
- semantic-extension audit;
- result/attempt manifests;
- engineering ledger;
- terminal verdict.

## Interpretation

Passing Test C supports the narrower empirical claim that the frozen runtime generalized to the preregistered independent domain under the stated non-inferiority and engineering-effort thresholds. It is not a claim of universal optimality for every decision problem.