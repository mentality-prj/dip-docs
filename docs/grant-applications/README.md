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
- applicant legal entity can satisfy the call;
- IP/security obligations are acceptable;
- the call does **not** require us to open-source QDIP Core, Canonical Decision IR, runtime, or engineer an artificial public/private split merely to protect QDIP IP.

## Current queue

### P0 — Canonical Evidence Pack

Always continue independently of a call. Current pack contains 01–19, with Test A result still pending primary execution and Test B/Test C protocols requiring freeze before use.

### P1 READY-WHEN-OPEN — Startup EDGE

Official USF status: next call **coming soon**; notification/pre-registration is open. Deep Tech explicitly includes AI/ML. Program page advertises up to EUR 20k pre-seed and EUR 40k seed.

QDIP fit: strong generic fit. No defence/LLM/agriculture distortion required.

Overlay: `startup-edge/`.

Official source: https://usf.com.ua/programs/startup-edge

## Explicitly dropped

- **BattleVerse OC1** — requires an additional LLM/defence-specific experiment outside the current QDIP execution priority. No further BattleVerse proposal, qualification or LLM integration work.
- **NOSTRADAMUS OC1** — requires an open-source digital application and an eligible incorporated business entity. We will not spend engineering effort designing how to separate or conceal QDIP IP to satisfy an open-source grant condition. The overlay is removed and no submission work is planned.

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
