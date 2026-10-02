# BattleVerse Open Call 1 — QDIP Application Overlay

Status checked: 2026-10-02
Program: EDF BattleVerse Open Call 1
Canonical technical evidence: `../../grant-evidence-pack/`
Priority: P0 conditional

## 1. Current call profile

Confirmed from the European Commission / BattleVerse call information:

- call open: 14 September 2026;
- deadline: 16 November 2026, 17:00 CET;
- applicants: SMEs/start-ups;
- eligible establishment: EU Member States, Norway or Ukraine;
- consortium: 1–3 beneficiaries, therefore single-applicant submission is permitted;
- duration: 6 months;
- funding: up to EUR 60,000 per beneficiary, up to EUR 180,000 per three-beneficiary experiment;
- target: innovative defence mission-planning, simulation, training and operations technologies.

Funding-rate/eligible-cost details must be revalidated from the official Guide for Applicants before budget freeze. Current call summaries report funding up to 100% of eligible costs, but the application budget must use the official guide as source of truth.

Official references:

- https://defence-industry-space.ec.europa.eu/edf-battleverse-project-launches-first-open-call-cascade-funding-2026-09-28_en
- https://battleverse-project.eu/open-calls/

## 2. Topic fit gate

QDIP can only target Topic 1.

Official Topic 1 is explicitly framed around:

> Large language models to support strategic decision-making, symbolic reasoning, game theory, and planning under uncertainty.

QDIP already has a substantive fit to the decision/problem side:

- strategic decision support;
- structured actions and constraints;
- symbolic/canonical decision representation;
- utility/risk-aware decisioning;
- planning under uncertainty;
- auditable recommendation generation;
- replay and outcome evaluation.

The unresolved issue is the LLM requirement.

## 3. GO / NO-GO decision

### GO only if

An LLM has a real technical function that cannot be replaced by a cosmetic wrapper, for example one or more of:

- translating commander/operator natural-language intent into a validated DecisionSpec;
- extracting candidate constraints/objectives from doctrine or scenario text and requiring deterministic validation before execution;
- generating candidate Courses of Action that are then checked/optimized by QDIP symbolic semantics;
- explaining/reconstructing decision alternatives while the formal runtime remains authoritative;
- supporting human-in-the-loop scenario reasoning while QDIP enforces feasibility, utility/risk and auditability.

In the proposed architecture the LLM must not be the decision authority:

```text
Human / scenario text
        ↓
LLM interpretation / CoA generation
        ↓
validated DecisionSpec
        ↓
Canonical Decision IR
        ↓
QDIP deterministic/stochastic decision runtime
        ↓
feasible plans / Pareto alternatives / audit
```

This is technically coherent with QDIP because the LLM handles unstructured semantic input while the runtime handles formal decision semantics.

### NO-GO if

- the only change is adding a chatbot or LLM-generated explanation;
- the application requires replacing QDIP's formal runtime with LLM reasoning;
- the proposed defence use case cannot produce a credible six-month experiment/demonstration;
- achieving fit requires changing the frozen Universal Runtime thesis;
- there is no genuine defence mission-planning scenario family available for validation.

No application should be written beyond fit analysis until the formal GO/NO-GO protocol passes.

The formal test is defined in:

- [01 — LLM → DecisionSpec Bounded Qualification Protocol](01-llm-decision-spec-mini-protocol.md)

It requires ambiguity handling, constraint/objective extraction, controlled abstention, provenance, deterministic validation, failure-mode analysis, manual-gold comparison, naive-LLM ablation, downstream QDIP decision-impact measurement and human-effort reduction. A plain text-to-JSON implementation is explicitly insufficient.

## 4. GO proof sequence

The BattleVerse GO decision cannot be based on one hand-picked mission scenario.

Required sequence:

1. **one development scenario** — smoke-test implementation and metric pipeline only;
2. finalize prompts, validators, ambiguity/abstention policy and failure taxonomy;
3. independently create/review the blind gold packages;
4. freeze S1/S2, gold hashes, QDIP runtime, deterministic scoring rubric, aggregation formulas and numerical GO thresholds;
5. execute **five heterogeneous blind scenarios** without tuning;
6. apply the preregistered mechanical GO/NO-GO gate.

The five blind cases form a **bounded qualification set**, not evidence of broad semantic generalization. The development scenario is exploratory and cannot support the GO verdict.

A BattleVerse application may proceed only if the bounded qualification test simultaneously demonstrates:

- critical-constraint recall at or above the frozen threshold;
- zero executable hallucinated hard constraints;
- controlled silent assumptions;
- zero extraction-induced hard-constraint violations;
- per-scenario and aggregate downstream semantic non-inferiority to manual gold;
- at least 30% total human structuring/review effort reduction across blind cases, with the per-case anti-regression cap;
- measurable safety/semantic advantage of S2 over naive LLM extraction S1 under absolute preregistered deltas;
- provenance and ambiguity-control thresholds;
- blind-set integrity with no omitted failures or post-freeze tuning.

If S2 wins only on the development scenario, only improves JSON formatting, or merely ties S1 at ceiling without measurable added value, the result is `BATTLEVERSE_NO_GO`.

## 5. Candidate experiment if GO

Working concept:

**LLM-to-Formal Mission Decision Runtime**

Research/engineering question:

> Can an LLM-supported interface convert ambiguous mission-planning intent and scenario information into formally validated decision problems, while QDIP provides symbolic constraint enforcement, planning under uncertainty, risk/utility evaluation and auditable Courses of Action?

Possible six-month scope after the pre-application GO proof:

1. expand the semantic-intake benchmark and scenario library beyond the bounded qualification set;
2. improve ambiguity detection, clarification and provenance mechanisms without weakening QDIP formal authority;
3. implement LLM → DecisionSpec constrained extraction/generation as a reusable front-end layer;
4. validate against Canonical Decision IR semantics;
5. generate/optimize feasible Courses of Action under uncertainty;
6. implement human-in-the-loop correction/rejection;
7. benchmark malformed/ambiguous input handling, constraint preservation, decision quality and operator effort;
8. deliver demonstrator and reproducibility/evidence package.

This must remain an application-specific experiment over the QDIP runtime, not a defence fork of QDIP Core.

## 6. Canonical evidence mapping

| BattleVerse need | QDIP source |
|---|---|
| formal/symbolic decision semantics | `../../grant-evidence-pack/05-architecture-canonical-ir.md` |
| planning under uncertainty | `03-research-hypothesis.md`, `04-methodology.md` |
| decision-quality evaluation | Test A/B/C benchmark methodology |
| explainability/audit | existing DIP/QDIP audit and DecisionResult documentation |
| reusable architecture | Canonical Decision IR + solver boundary |
| TRL evidence | Evidence Pack TRL material |
| risk/IP/team | shared canonical evidence modules |

BattleVerse-specific LLM/defence experiment claims belong only in this overlay and must not contaminate generic QDIP claims.

## 7. Application work if GO

Before submission:

1. archive official Guide for Applicants and template;
2. verify funding rate, eligible costs, ownership-control requirements and applicant legal eligibility;
3. select exact Topic 1 interpretation and defence scenario family;
4. specify LLM role and model/provider constraints;
5. define current TRL and credible end-of-experiment TRL target;
6. produce six-month WP/milestone/deliverable plan;
7. map EUR 60k budget to eligible costs;
8. prepare experiment architecture and demo plan;
9. prepare risk/security/dual-use/data handling section;
10. complete mandatory declarations/ownership-control documentation;
11. produce official-template proposal in English;
12. perform evaluator-style red-team review before submission.

Budget work starts only after the official Guide for Applicants confirms the funding-rate and eligible-cost assumptions.

## 8. Decision deadline

Resolve the QDIP ↔ Topic 1 fit immediately, well before the 16 November 2026 submission deadline.

If NO-GO, stop all BattleVerse-specific work and move Startup EDGE to the top application priority. The Canonical Evidence Pack continues regardless of this decision.
