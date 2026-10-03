# 07 — Test A Results and Evidence Manifest

Status: **PENDING PRIMARY EXECUTION**

This document is the canonical results surface for Test A — Readiness Recovery. It must never contain invented, estimated, or development-only numbers presented as primary evidence.

## Purpose

Test A is the first empirical check of the QDIP Universal Decision Runtime thesis. It evaluates two independent gates:

```text
NR_QDIP^(A) <= NR_specialized^(A) + epsilon_A
E_domain,QDIP^(A) <= 0.5 * E_domain,specialized^(A)
```

Decision-quality non-inferiority and engineering-effort reduction are reported separately.

## Required execution identity

Before results are accepted, record:

- benchmark specification/version/hash;
- methodology hash;
- qualified implementation hash;
- QDIP Core / Canonical IR / extension API commit or immutable reference;
- specialized baseline identity and commit;
- scenario/input/seed set identity;
- `S_A`, `epsilon_A`, reference hierarchy and statistical procedure;
- compute/information-budget equivalence statement;
- engineering-effort taxonomy and evidence rules;
- immutable attempt ledger location.

## Primary result table

| Metric | QDIP | Specialized baseline | Gate | Result |
|---|---:|---:|---|---|
| Reference-normalized regret/loss | PENDING | PENDING | `NR_QDIP <= NR_specialized + epsilon_A` | PENDING |
| Domain-marginal engineering effort | PENDING | PENDING | `E_QDIP <= 0.5 E_specialized` | PENDING |
| Feasibility / hard-constraint violations | PENDING | PENDING | frozen benchmark rule | PENDING |
| Audit/replay completeness | PENDING | PENDING | frozen benchmark rule | PENDING |

## Engineering-effort ledger

Report observed evidence-backed effort in the frozen categories:

```text
E_domain = E_model + E_impl + E_test + E_integration + E_deployment + E_audit
```

Each category must link to evidence such as commits, PRs, task records, test artifacts, deployment/config changes or audit artifacts. Do not use retrospective unsupported hour estimates as primary evidence.

Also report cumulative economics separately:

```text
E_cumulative,QDIP = E_core_IR_runtime + sum(E_domain,QDIP)
E_cumulative,specialized = sum(E_domain,specialized)
```

## Invalidity report

List every attempt and classify it under the frozen invalidity taxonomy. A result-affecting post-freeze semantic change, unequal information/compute budget, scenario/seed substitution, baseline-scope change or result-driven tuning invalidates the affected primary evidence.

## Terminal interpretation

Test A can produce evidence of viability or falsification for Domain A. It does **not** by itself establish cross-domain universality. Cross-domain evidence requires Test B and blind Test C.

## Grant-use rule

Until primary execution is complete, applications may state that Test A is preregistered and implementation/evidence work is underway. They must not state a PASS, percentage saving, regret improvement or engineering reduction as established fact.