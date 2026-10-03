# QDIP Universal Runtime — Grant Evidence Pack

Status: active canonical grant/R&D evidence package

This directory is the single source of truth for the QDIP Universal Decision Runtime research/product thesis and its evidence. Grant-specific applications must remain thin overlays under `../grant-applications/`.

## Central thesis

QDIP is not positioned as another BI platform, ERP suite, chatbot or novel mathematical solver. The research/product claim is that a reusable decision runtime can preserve decision quality relative to specialized implementations while materially reducing domain-marginal engineering effort.

For each validation domain `d ∈ {A, B, C}`:

```text
NR_QDIP^(d) <= NR_specialized^(d) + epsilon_d
E_domain,QDIP^(d) <= 0.5 * E_domain,specialized^(d)
```

The criteria are independent. `NR` is pre-registered reference-normalized regret/loss. The 50% engineering threshold is a pre-registered product-materiality threshold, not a universal constant.

## Cumulative economics

Do not hide the up-front reusable-platform cost:

```text
E_cumulative,QDIP = E_core_IR_runtime + sum(E_domain,QDIP)
E_cumulative,specialized = sum(E_domain,specialized)
```

## Freeze rule

Before primary benchmark execution freeze and record Core/IR/API identity, baseline implementations/scope, scenarios/seeds/evaluation horizon, `S_d`, `epsilon_d`, reference hierarchy, statistics, invalidation rules, compute/information budgets and engineering-accounting rules. Verdict-affecting post-freeze changes require a new versioned evidence chain.

## Validation sequence

1. Test A pre-registration — Readiness Recovery.
2. Canonical Decision IR stabilization.
3. freeze Core / IR / extension API.
4. Test A primary execution.
5. Test B — Procurement.
6. Blind Test C — independent operational domain.
7. consolidated generalization and cumulative-economics evidence.
8. external relevant-environment validation where available.

## Evidence pack

| ID | Document | Status |
|---|---|---|
| 01 | [Executive Summary](01-executive-summary.md) | active |
| 02 | [State of the Art](02-state-of-the-art.md) | active |
| 03 | [Research Hypothesis](03-research-hypothesis.md) | active |
| 04 | [Methodology](04-methodology.md) | active |
| 05 | [Architecture + Canonical Decision IR](05-architecture-canonical-ir.md) | active |
| 06 | [Test A Pre-registration Protocol](06-test-a-protocol.md) | active |
| 07 | [Test A Results / Evidence Manifest](07-test-a-results.md) | template ready; primary result pending |
| 08 | [Test B Procurement Protocol](08-test-b-procurement.md) | protocol draft; freeze before execution |
| 09 | [Blind Test C Generalization Protocol](09-test-c-blind-generalization.md) | protocol draft; freeze before reveal |
| 10 | [TRL Roadmap](10-trl-roadmap.md) | ready |
| 11 | [Work Packages](11-work-packages.md) | ready |
| 12 | [Budget Framework](12-budget-framework.md) | ready; program-specific budgets in overlays |
| 13 | [Risk Register](13-risk-register.md) | ready |
| 14 | [IP / FTO](14-ip-fto.md) | working module; legal review where material |
| 15 | [Exploitation / Business Model](15-exploitation-business-model.md) | ready as hypothesis/evidence framework |
| 16 | [Ukrainian / EU Impact](16-ukraine-eu-impact.md) | ready |
| 17 | [Team](17-team.md) | partially populated; legal/CV fields TBD |
| 18 | [Validation Partner / LOI](18-validation-loi.md) | template ready |
| 19 | [Evidence Appendix](19-evidence-appendix.md) | ready |

## Grant overlays

See:

- [`../grant-applications/README.md`](../grant-applications/README.md)
- [`../grant-applications/target-register.md`](../grant-applications/target-register.md)
- [`../grant-applications/startup-edge/`](../grant-applications/startup-edge/)
- [`../grant-applications/nostradamus-oc1/`](../grant-applications/nostradamus-oc1/)
- [`../grant-applications/battleverse-oc1/`](../grant-applications/battleverse-oc1/)

## Reuse and truth rules

Existing repository documents remain source material. Do not duplicate validated material unless a specific application needs a concise evaluator-facing adaptation. Results not yet produced remain `PENDING`, `PREREGISTERED`, `DEVELOPMENT`, `HYPOTHESIS` or `TBD` as appropriate.

External validation/LOI is desirable evidence, but it does not need to create a consortium dependency unless the call explicitly requires one.