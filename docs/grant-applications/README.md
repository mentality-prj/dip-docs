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

## Active priority queue

### P0 — BattleVerse Open Call 1

Status: open. Deadline: 16 November 2026, 17:00 CET.

Proceed only if QDIP has a genuine fit to BattleVerse Topic 1 without distorting the product thesis. Topic 1 is explicitly framed around large language models supporting strategic decision-making, symbolic reasoning, game theory and planning under uncertainty.

Decision rule:

- GO only if an LLM layer has a necessary, technically defensible role in a defence decision-support experiment built on QDIP;
- NO-GO if the proposal would add an artificial LLM wrapper solely to satisfy the topic wording;
- the underlying QDIP Universal Runtime thesis must remain unchanged.

Application overlay: `battleverse-oc1/`.

### P0 parallel — QDIP Canonical Evidence Pack

Not a grant application. Continue the evidence program independently of any call:

`Test A preregistration → Test A results → Test B Procurement → blind Test C → TRL/WP/Risks/IP-FTO/Exploitation/Impact/Team/LOI`.

This work must not be delayed by grant-specific narrative work.

### P1 — Startup EDGE

Primary generic grant target for QDIP. DeepTech explicitly includes AI/ML and does not require a defence-specific or LLM-specific reframing.

Target state before the next call opens: 80–90% application readiness, including eligibility assumptions, stage selection, use-of-funds scenarios, milestones, market/traction, team, pitch deck structure and application-answer bank.

Application overlay: `startup-edge/`.

### P2 — Future solo / full-funding calls only

Create a new overlay only when a concrete call is identified and passes the financial/structural gate:

- single applicant permitted;
- no mandatory consortium;
- no required own contribution / target funding compatible with the QDIP financing rule;
- technical scope genuinely fits QDIP without product distortion.

Do not prepare speculative overlays in advance.

## Stopped / inactive targets

Do not spend application-writing effort on these under the current financing/structure gate:

- EIC Pathfinder — mandatory consortium for the relevant route;
- Eurostars — consortium required;
- EIC Accelerator — beneficiary contribution required for the grant component under the current target structure;
- PARP Ścieżka SMART — own contribution required at applicable SME R&D funding intensities.

Existing material may remain as reusable reference material, but these programs are not in the active application queue.
