# Grant Applications — Program-Specific Overlays

Status checked: **2026-10-03**

This directory contains thin application layers on top of `docs/grant-evidence-pack/`.

## Hard gate

Do not spend proposal effort unless all mandatory conditions pass:

- funding is real non-repayable project/R&D/startup financing, not a hackathon, bootcamp, pitch prize or award;
- single applicant / mono-beneficiary is permitted;
- no mandatory consortium;
- no mandatory own-cash co-financing;
- no loan, repayable advance, revenue repayment, grant-equivalent repayment, mandatory tax/social-contribution return or other economic-return obligation tied to the funding;
- no mandatory equity transfer;
- technical scope fits QDIP without changing the Universal Runtime thesis or inventing a grant-specific use case;
- applicant legal entity can satisfy the call;
- IP/security/open-science obligations are acceptable;
- the call does **not** require us to open-source QDIP Core, Canonical Decision IR, runtime, or engineer an artificial public/private split merely to protect QDIP IP.

## Current queue

### P0 — Canonical Evidence Pack

Always continue independently of a call. Current pack contains 01–19, with Test A result still pending primary execution and Test B/Test C protocols requiring freeze before use.

### P0 APPLY-NOW — EIC Pathfinder Challenges 2026 / DeepRAP

Official EIC status: **OPEN**, deadline **2026-10-28 17:00 Brussels local time**. Pathfinder Challenges allow a single-applicant route and fund up to EUR 4m at 100% of eligible costs.

QDIP fit: high at the thematic level because DeepRAP targets deep reasoning, abstraction, planning and trustworthy cognitive AI. Stage fit is conditional: Pathfinder is early-stage high-risk research, so QDIP should apply only with a genuine low-TRL breakthrough research hypothesis, not ordinary product development or commercialization.

Official sources:
- https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder/eic-pathfinder-challenges-2026_en

### P1 READY-WHEN-OPEN — Startup EDGE

Official USF status: next call **coming soon**; notification/pre-registration is open. Deep Tech explicitly includes AI/ML. Program page advertises up to EUR 20k pre-seed and EUR 40k seed.

QDIP fit: strong generic fit. No defence/LLM/agriculture distortion required.

Overlay: `startup-edge/`.

Official source: https://usf.com.ua/programs/startup-edge

### P1 WATCH — FFplus Business Experiments Call 3

Official FFplus status: third Business Experiments call is scheduled to open in **January 2027**. Call-3 funding/eligibility details are not yet frozen here and must be revalidated when the call opens.

QDIP fit: potentially strong only if there is a genuine HPC-enabled business experiment (for example large-scale scenario/optimization/uncertainty evaluation). Do not introduce HPC merely to qualify.

Official source: https://www.ffplus-project.eu/en/open-call/business-experiments/

### P2 WATCH — PARP Startup Booster Poland / Tech Impact

PARP requires selected accelerators to open their first startup recruitment no later than **2027-02-01**. Support to an individual startup may include up to **PLN 400k as a grant** during acceleration. Startup support is de minimis aid and detailed terms will depend on the selected accelerator round.

QDIP fit: plausible if the economic-impact case is accepted naturally. Revalidate each operator's startup eligibility, cash-flow, IP and financing conditions before proposal work.

Official source: https://www.parp.gov.pl/component/qnadb/kategoria/startup-booster-poland-tech-impact

## Discovery only

- **EIT AI Growth Studio** — do not allocate proposal work until an official call page and binding financing terms are located and verified. Earlier secondary references are insufficient.

## Explicitly dropped

- **EIT AI Entrepreneurs Lab** — bootcamp/pitch-prize model; not project financing for QDIP.
- **Власна справа 2.0** — fails the current economic-return gate because its fiscal/employment obligations make it unsuitable for the financing strategy even though it is formally a grant.
- **BattleVerse OC1** — requires an additional LLM/defence-specific experiment outside the current QDIP execution priority. No further BattleVerse proposal, qualification or LLM integration work.
- **NOSTRADAMUS OC1** — requires an open-source funded application and an eligible incorporated business entity. We will not spend engineering effort designing how to separate or conceal QDIP IP to satisfy an open-source grant condition.

## Watch / rejected under current gate

- **I3FLOAT OC1** — solo/100% funding is attractive, but scope is floating offshore wind TRL 6–8; no natural QDIP application is currently evidenced.
- **FIERCE OC2** — 100% voucher, but requires downstream space-data/green transformation; no current QDIP wedge.
- **NLnet Restack** — AI-related projects are generally out of scope and funded outputs are FOSS; not a current QDIP target.
- **RENEW BOOSTER OC2** — private co-financing required.
- **Water4All / many joint calls** — mandatory multi-country consortium.
- **Brave1 International NATO** — current call requires an eligible NATO-country partner and is focused on counter-UAS.
- **EIC Pathfinder Open** — consortium required; this does **not** apply to Pathfinder Challenges, where single applicants are allowed.
- **Eurostars** — consortium required.
- **PARP Ścieżka SMART / EIC Accelerator / EIC Pre-Accelerator** — beneficiary contribution and/or financing structure fails the current no-own-co-financing gate.

## Application architecture

```text
Canonical Evidence Pack
        ↓
program eligibility + financing/IP gate
        ↓
program-specific concept / WPs / budget / forms
        ↓
submission package
```

Do not fork the thesis, benchmark evidence, Canonical Decision IR, core IP position or experiment manifests for a grant.
