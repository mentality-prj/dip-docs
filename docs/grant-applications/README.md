# Grant Applications — Program-Specific Overlays

This directory contains thin program-specific application layers built on top of the canonical evidence base in `docs/grant-evidence-pack/`.

## Rule

Do not duplicate or fork the research thesis, methodology, benchmark evidence, Canonical Decision IR specification, TRL evidence, IP position, or core technical narrative for each grant.

Use:

```text
Canonical Evidence Pack
        ↓
Program-specific mapping / eligibility / narrative / budget / forms
        ↓
Submitted application
```

The canonical source of truth remains:

- `docs/grant-evidence-pack/`
- relevant `docs/research/`
- relevant `docs/proposal/`
- relevant `docs/operations/`

## What belongs in each program folder

Each grant/application folder may contain:

1. program profile and current call status;
2. eligibility checklist;
3. evaluator/selection criteria mapping;
4. QDIP-to-program fit;
5. stage/TRL positioning;
6. application-specific executive summary;
7. requested budget and eligible-cost mapping;
8. answers/forms required by that call;
9. pitch deck/pitch script mapping;
10. application checklist and submission evidence.

## What must not be copied

Do not create program-specific variants of:

- the central Universal Runtime thesis;
- Test A/B/C methodology;
- Canonical Decision IR semantics;
- benchmark results;
- core IP/FTO evidence;
- experiment manifests.

If a grant requires different wording, link to the canonical evidence and write a concise program-facing adaptation rather than a second scientific source of truth.

## Current targets

- `startup-edge/` — Ukrainian Startup Fund Startup EDGE, DeepTech fit.
- Additional target programs should receive their own sibling directory only after the program is confirmed as an actual application target.
