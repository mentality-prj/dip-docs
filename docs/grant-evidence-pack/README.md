# QDIP Universal Runtime — Grant Evidence Pack

Status: active canonical grant/R&D evidence package

This directory is the single source of truth for the QDIP Universal Decision Runtime research/product thesis and its evidence.

Grant-specific applications must not fork this package. They live under `../grant-applications/` as thin overlays containing eligibility, evaluator mapping, program-specific narrative, budget/forms and submission artifacts.

## Central thesis

QDIP is not positioned as another BI platform, ERP suite, or novel mathematical solver. The research/product claim is that a reusable decision runtime can preserve decision quality relative to specialized implementations while materially reducing domain-marginal engineering effort.

For each validation domain `d ∈ {A, B, C}` the primary empirical gate is:

```text
NR_QDIP^(d) <= NR_specialized^(d) + epsilon_d
E_domain,QDIP^(d) <= 0.5 * E_domain,specialized^(d)
```

where:

- `NR` is pre-registered reference-normalized regret/loss;
- `epsilon_d` is the domain-specific non-inferiority margin fixed before evaluation;
- `E_domain` is observed incremental engineering effort across modeling, implementation, testing, integration, deployment, and auditability.

The `50%` engineering threshold is a pre-registered MVP/product materiality threshold, not a universal mathematical constant.

The two primary criteria are evaluated independently. They are not collapsed into a single weighted score.

## Cumulative economics

The reusable QDIP platform has an up-front Core/IR/runtime engineering cost. That cost must not be hidden by the marginal-domain comparison.

Report separately:

```text
E_cumulative,QDIP = E_core_IR_runtime + sum(E_domain,QDIP)
E_cumulative,specialized = sum(E_domain,specialized)
```

This secondary economic analysis estimates the break-even point of the reusable runtime across domains.

## Freeze rule

Before primary benchmark execution, freeze and record:

- QDIP Core version/commit;
- Canonical Decision IR semantics/schema;
- extension API;
- baseline implementations and scope;
- scenarios, seeds and evaluation horizon;
- `S_d`, `epsilon_d`, and reference hierarchy;
- statistical test and invalidation rules;
- engineering scope/accounting rules.

Any post-freeze semantic change to Core/IR/API invalidates primary evidence for the affected test.

## Validation sequence

1. Test A pre-registration — Readiness Recovery.
2. Canonical Decision IR stabilization.
3. Freeze Core / IR / extension API.
4. Test A — Readiness Recovery benchmark.
5. Test B — Procurement.
6. Blind Test C — independent operational domain selected using a pre-registered mechanism.
7. Consolidated generalization and cumulative-economics evidence.

## Evidence pack

| ID | Document | Status |
|---|---|---|
| 01 | [Executive Summary](01-executive-summary.md) | initial |
| 02 | [State of the Art](02-state-of-the-art.md) | initial |
| 03 | [Research Hypothesis](03-research-hypothesis.md) | initial |
| 04 | [Methodology](04-methodology.md) | initial |
| 05 | [Architecture + Canonical Decision IR](05-architecture-canonical-ir.md) | initial |
| 06 | [Test A Pre-registration Protocol](06-test-a-protocol.md) | initial |
| 07 | Test A Results | pending experiment |
| 08 | Test B Procurement | pending |
| 09 | Test C Blind Generalization | pending |
| 10 | TRL Roadmap | reuse/update from `docs/research` and `docs/grant` |
| 11 | Work Packages | reuse/update from `docs/grant/42-work-packages.md` |
| 12 | Budget | reuse/update from proposal/grant budget docs |
| 13 | Risks | reuse/update from `docs/operations/risk-register.md` |
| 14 | IP / FTO | reuse/update from `docs/research/07-ip-strategy.md` |
| 15 | Exploitation / Business Model | pending update |
| 16 | Ukrainian / EU Impact | pending update |
| 17 | Team | pending update |
| 18 | Validation Partner / LOI | pending |
| 19 | Evidence Appendix | pending |

## Grant-specific application overlays

Program-specific materials belong in:

- [`../grant-applications/README.md`](../grant-applications/README.md)
- [`../grant-applications/startup-edge/README.md`](../grant-applications/startup-edge/README.md)

Future grants should receive sibling directories only when they become actual application targets.

## Reuse policy

Existing repository documents remain source material. Do not duplicate validated material unless a specific application needs a concise evaluator-facing adaptation. The previous `docs/rd-grant-package` describes an older behavioral-risk research direction and is not the canonical QDIP Universal Runtime thesis.

## Required external evidence

Before major R&D grant submission target at least one external validation partner / LOI in readiness, procurement, logistics, fleet, inventory, or resource allocation. The partner is evidence of operational relevance; it does not need to be a consortium member unless a specific call requires it.
