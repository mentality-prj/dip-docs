# Grant Applications — Program-Specific Overlays

Status checked: **2026-10-03**

This directory contains thin application layers on top of `docs/grant-evidence-pack/`.

## Hard gate

Do not spend proposal effort unless all mandatory conditions pass:

- single applicant is permitted;
- no mandatory consortium;
- no mandatory own-cash co-financing;
- funding is non-repayable/FSTP/grant/prize and cash-flow is executable;
- technical scope fits QDIP without changing the Universal Runtime thesis;
- applicant legal entity can satisfy the call.

## Current queue

### P0 — Canonical Evidence Pack

Always continue independently of a call. Current pack contains 01–19, with Test A result still pending primary execution and Test B/Test C protocols requiring freeze before use.

### P1 READY-WHEN-OPEN — Startup EDGE

Official USF status: next call **coming soon**; notification/pre-registration is open. Deep Tech explicitly includes AI/ML. Program page advertises up to EUR 20k pre-seed and EUR 40k seed.

QDIP fit: strong generic fit. No defence/LLM/agriculture distortion required.

Overlay: `startup-edge/`.

Official source: https://usf.com.ua/programs/startup-edge

### P1 OPEN-CONDITIONAL — NOSTRADAMUS Open Call #1

Open now; deadline **2 December 2026, 17:00 CET**. A single SME/start-up/small mid-cap business entity may apply. Up to EUR 50k/project; requested contribution must represent 100% of project costs. The open call funds open-source farm decision applications and Topic 5 explicitly covers integrated cross-domain decision-support applications combining at least two agriculture topics.

QDIP fit: credible only as a grant-specific agriculture adapter/application over unchanged Core. GO requires acceptable open-source/IP terms, eligible applicant entity, starting TRL eligibility and a defensible agriculture validation plan.

Overlay: `nostradamus-oc1/`.

Official source: https://nostradamus-project.eu/open-call-1/

## Explicitly dropped

- **BattleVerse OC1** — removed from the grant strategy. It requires an additional LLM/defence-specific experiment that is outside the current QDIP execution priority. No further BattleVerse proposal, qualification or LLM integration work should be scheduled unless this decision is explicitly revisited.

## Watch / rejected under current gate

- **I3FLOAT OC1** — solo/100% funding is attractive, but scope is floating offshore wind TRL 6–8; no natural QDIP application is currently evidenced. Do not distort product for it.
- **FIERCE OC2** — 100% voucher, but requires downstream space-data/green transformation; no current QDIP wedge.
- **NLnet Restack** — 100% and solo-friendly, but AI-related projects are generally out of scope and all outputs are FOSS; not a current QDIP target.
- **RENEW BOOSTER OC2** — requires 30–50% private co-funding depending on grant size; reject under financing gate.
- **Water4All / many joint calls** — mandatory multi-country consortium; reject under solo gate.
- **Brave1 International NATO** — current call requires an eligible NATO-country partner and is focused on counter-UAS; reject under solo/product-fit gate.
- **PARP Ścieżka SMART / EIC Accelerator / EIC Pre-Accelerator** — own contribution required under relevant funding structure; inactive under current rule.
- **EIC Pathfinder / Eurostars** — mandatory consortium; inactive.

## Application architecture

```text
Canonical Evidence Pack
        ↓
program eligibility + evaluator mapping
        ↓
program-specific concept / WPs / budget / forms
        ↓
submission package
```

Do not fork the thesis, benchmark evidence, Canonical Decision IR, core IP position or experiment manifests for a grant.