# NOSTRADAMUS Open Call #1 — QDIP Application Overlay

Status checked: **2026-10-03**
Status: **OPEN-CONDITIONAL**
Canonical evidence: `../../grant-evidence-pack/`

## 1. Official call profile

NOSTRADAMUS OC1 funds open-source digital applications for sustainable and efficient agriculture/farm decision-making.

Official current facts:

- deadline: **2 December 2026, 17:00 CET**;
- duration: **12 months**;
- selected projects: 5;
- funding: **up to EUR 50,000/project**;
- requested contribution must represent **100% of project costs**, including indirect costs;
- support: FSTP lump sum paid across four programme sprints;
- application may be submitted by a single legal entity or a consortium of max two;
- a single applicant must be a business entity: SME, start-up or small mid-cap;
- proposed solution must align with exactly one call topic;
- the application must use the NOSTRADAMUS platform architecture and meet the official starting-TRL/geographical requirements;
- application: F6S form + mandatory technical proposal template.

Official source and documents:
https://nostradamus-project.eu/open-call-1/

## 2. QDIP fit

The only natural target is **Topic 5 — Open Topic**, which requires an integrated cross-domain decision-support application combining at least two of Topics 1–4.

Candidate concept:

**QDIP Agro Decision Runtime — integrated crop/water/soil operational decision support on the NOSTRADAMUS platform.**

Example bounded combination:

- T1 crop-production optimisation under changing climate/soil conditions;
- T3 water-resource efficiency and drought resilience;

or T2 soil/nutrient management + T3 water efficiency if platform/data support makes that combination stronger.

QDIP Core remains unchanged:

```text
NOSTRADAMUS data/services
        ↓
agriculture domain adapter
        ↓
DecisionSpec / Canonical Decision IR
        ↓
QDIP validation + uncertainty + utility/risk + solver
        ↓
open grant-specific farm decision application
        ↓
recommendation + audit + realized-outcome evaluation
```

## 3. GO / NO-GO gate

Proceed only if all are PASS:

1. applicant legal entity is eligible;
2. starting TRL satisfies the official call definition with evidence;
3. required open-source output can be delivered without unacceptable exposure of unrelated QDIP Core/background IP;
4. at least two agriculture topics can be integrated using credible NOSTRADAMUS data/components;
5. a farm decision problem with measurable agronomic/economic outcome can be defined;
6. the EUR 50k/12-month scope is executable without mandatory own cash contribution;
7. platform integration requirements are technically feasible;
8. agriculture work is implemented as adapter/application, not a fork of Core.

If any mandatory item fails, do not submit merely because the funding rate is attractive.

## 4. Research/product value to QDIP

This grant can create a real fourth application domain and external platform integration. It can strengthen QDIP only if it produces reusable evidence of lower integration effort and valid decisions.

Important: once an agriculture adapter is developed before blind Test C freeze/reveal, agriculture must be excluded from the Test C blind candidate pool. NOSTRADAMUS evidence may be additional external-domain evidence, not retroactively labelled blind Test C.

## 5. Candidate 12-month work plan

### Sprint/WP1 — Training + technical binding
- validate applicant/TRL/IP requirements;
- map NOSTRADAMUS platform/data services;
- freeze agriculture decision problem and economic/agronomic KPIs.

### Sprint/WP2 — Design
- agriculture DecisionSpec/domain adapter;
- Canonical IR mapping;
- baseline/comparator and validation design;
- UX/human decision workflow.

### Sprint/WP3 — Development and validation
- implement open grant-specific application;
- integrate at least two call-topic data streams/services;
- execute benchmark/pilot cases;
- measure decision validity, outcome proxy/realized outcome where available and integration effort;
- harden audit/replay.

### Sprint/WP4 — Demonstration and assessment
- demonstrator;
- reproducibility/evidence pack;
- user/domain validation;
- exploitation plan and QDIP reuse assessment.

## 6. Budget framework — max EUR 50k

Freeze only after reading the official Guidelines/Sub-grant Agreement.

Priority budget categories:
- R&D/engineering personnel;
- NOSTRADAMUS integration and application development;
- data/compute/testing where eligible;
- domain validation/user testing;
- mandatory demonstration/reporting.

Subcontracting must not be assumed eligible. Payment timing must be included in cash-flow planning.

## 7. IP/open-source boundary

The call explicitly targets open-source digital applications. Before submission identify:

- what grant-specific source must be published;
- licence required/allowed;
- background-IP treatment in the Sub-grant Agreement;
- whether the agriculture adapter/application can be open while QDIP Core remains separately licensed;
- data/model redistribution restrictions.

Unacceptable forced disclosure of Core is a NO-GO condition.

## 8. Submission checklist

- [ ] download/archive Guidelines, Technical Specification, proposal template and agreement
- [ ] applicant entity eligibility PASS
- [ ] geographical eligibility PASS
- [ ] starting TRL evidence PASS
- [ ] choose exactly Topic 5 and exact two+ subtopics
- [ ] confirm open-source/IP architecture
- [ ] define farm decision owner/user and validation case
- [ ] define baseline and measurable outcome
- [ ] map NOSTRADAMUS platform components
- [ ] prepare technical proposal in official template
- [ ] complete F6S answers
- [ ] produce EUR 50k cost/resource justification
- [ ] red-team evaluator review
- [ ] submit before 2 Dec 2026 17:00 CET