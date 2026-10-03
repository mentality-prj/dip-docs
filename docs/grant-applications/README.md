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

### P0 WATCH — PARP Startup Booster Poland / DeepTech Goes Dual

PARP has completed the operator application window and is evaluating accelerator proposals. The programme is structurally close to QDIP: it funds deep-tech startups from technology development toward commercialisation. Dual-use is a portfolio priority, not a requirement for every startup: current operator rules require at least 30% of participants to be dual-use.

Published startup support ceilings are up to PLN 450k grant in Stage I plus up to PLN 450k grant in Stage II, capped at EUR 200k equivalent total grant per startup. Stage I must advance technology by at least two TRL levels to at least TRL6; Stage II prepares successful startups for market entry/commercialisation.

Do not treat this as APPLY-NOW until selected accelerators publish startup rounds and their startup agreements are checked for applicant form, cash-flow, IP, de minimis and own-contribution terms.

Official sources:
- https://www.parp.gov.pl/component/grants/grants/startup-booster-poland-deeptech-goes-dual
- https://www.parp.gov.pl/component/qnadb/kategoria/na-start/startup-booster-poland-deeptech-goes-dual

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

## Open but conditional

- **PARP StartupsExchange by StartSmart CEE** — current round is open through 2026-10-30 and covers up to 100% of eligible costs. However, only up to PLN 20k is a direct cash grant and up to PLN 80k is accelerator services; it also requires a Polish startup and is primarily an internationalisation programme. It is not an exact-fit QDIP R&D target under the current strategy.

## Discovery only

- **EIT AI Growth Studio** — do not allocate proposal work until an official call page and binding financing terms are located and verified. Earlier secondary references are insufficient.

## Explicitly dropped

- **EIC Pathfinder Challenges 2026 / DeepRAP** — financing mechanics pass, but the scientific scope does not. A competitive proposal would require QDIP to adopt a new low-TRL cognitive-AI reasoning/planning thesis instead of executing the frozen Universal Runtime thesis. That is grant-driven R&D and fails the Economic Value Gate.
- **EIT AI Entrepreneurs Lab** — bootcamp/pitch-prize model; not project financing for QDIP.
- **Власна справа 2.0** — fails the current economic-return gate because its fiscal/employment obligations make it unsuitable for the financing strategy even though it is formally a grant.
- **BattleVerse OC1** — requires an additional LLM/defence-specific experiment outside the current QDIP execution priority.
- **NOSTRADAMUS OC1** — requires an open-source funded application and an eligible incorporated business entity; conflicts with current QDIP IP/product-focus gate.

## Watch / rejected under current gate

- **I3FLOAT OC1** — solo/100% funding is attractive, but scope is floating offshore wind TRL 6–8; no natural QDIP wedge.
- **FIERCE OC2** — 100% voucher, but requires downstream space-data/green transformation; no current QDIP wedge.
- **NLnet Restack** — AI-related projects are generally out of scope and funded outputs are FOSS; not a current QDIP target.
- **RENEW BOOSTER OC2** — private co-financing required.
- **Water4All / many joint calls** — mandatory multi-country consortium.
- **Brave1 International NATO** — current call requires an eligible NATO-country partner and is focused on counter-UAS.
- **EIC Pathfinder Open** — consortium required.
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
