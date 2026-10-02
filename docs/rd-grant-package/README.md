# R&D Grant Package — Legacy Behavioral-Risk Package

> **Legacy / source material.** This package describes the earlier wellbeing / behavioral-risk research direction and is no longer the canonical QDIP grant thesis.
>
> Current package: [QDIP Universal Runtime — Grant Evidence Pack](../grant-evidence-pack/README.md).

The documents in this directory are retained for traceability, historical R&D evidence, reusable methodology fragments, and possible Dzvin/Mentality-specific work. They must not be used as the current QDIP Universal Runtime grant claim without explicit adaptation.

## Original purpose

Universal package intended for adaptation to different grant programs. The original scientific problem centered on individual behavioral-risk estimation, personalized baselines, uncertainty intervals and minimax evaluation.

## Existing files

| File | Original content | Current use |
|---|---|---|
| [A-scientific-problem-statement.md](A-scientific-problem-statement.md) | Behavioral-risk scientific problem, hypotheses and model | legacy/domain-specific source |
| [B-rd-work-plan.md](B-rd-work-plan.md) | R&D work plan for adaptive-risk model | legacy/source for WP structure only |
| [C-experimental-methodology.md](C-experimental-methodology.md) | Behavioral-risk datasets, baselines and statistical tests | methodology fragments only; not current protocol |
| [F-innovation-analysis.md](F-innovation-analysis.md) | Innovation analysis against wellbeing/risk approaches | legacy; replace with Universal Runtime state of the art |
| [G-budget-structure.md](G-budget-structure.md) | Budget structure | reusable after call-specific adaptation |

## Current canonical thesis

The Universal Runtime package tests, for each mandatory domain `d`:

```text
NR_QDIP^(d) <= NR_specialized^(d) + epsilon_d
E_QDIP^(d) <= 0.5 * E_specialized^(d)
```

with frozen Core, Canonical Decision IR semantics and extension API, and with Test C acting as the blind generalization test.

See:

- [Executive Summary](../grant-evidence-pack/01-executive-summary.md)
- [Research Hypothesis](../grant-evidence-pack/03-research-hypothesis.md)
- [Methodology](../grant-evidence-pack/04-methodology.md)
- [Canonical Decision IR](../grant-evidence-pack/05-architecture-canonical-ir.md)
- [Test A Pre-registration](../grant-evidence-pack/06-test-a-protocol.md)
