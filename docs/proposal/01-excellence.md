# 01 Excellence

Мова: Українська (default) | [English](01-excellence.en.md)

> **Технічне джерело:** [docs/research/11-rd-technical-dossier.md](../research/11-rd-technical-dossier.md)
> Математика, архітектура, чисельні приклади — звідти. Нижче — грантова структура з прив'язкою до секцій.

## 1.1 Vision and Objectives

**Chain of evidence:**

```
Existing system (Dzvin.co + DIP MVP)
    ↓ mathematical problem (heuristic weights, no personalised baseline)
    ↓ proposed method (state vector, minimax, hybrid governance)
    ↓ scientific novelty (claims N1–N5)
    ↓ verification (H1–H5, EXP-001–005)
    ↓ expected result (TRL 4→7, publications, platform reuse)
```

Source:

- docs/grant/01-vision.md
- docs/grant/02-problem-statement.md
- docs/research/11-rd-technical-dossier.md §1

## 1.2 Beyond State of the Art

**Key differentiation:**

- Wellbeing platforms: static dashboards; this system: 5-dimensional state vectors with minimax risk bounds
- MLOps platforms: no domain-specific governance for mental wellbeing
- Heuristic components (surrogate regression, manual weights) are research targets, not claims

Source:

- docs/grant/03-state-of-the-art.md
- docs/grant/04-scientific-novelty.md
- docs/research/11-rd-technical-dossier.md §3, §4

## 1.3 Scientific Hypotheses and Methods

| H   | Statement                                | Experiment  | Key metric              |
| --- | ---------------------------------------- | ----------- | ----------------------- |
| H1  | Hybrid > ML-only and rules-only          | EXP-HYB-002 | AUROC, false alert rate |
| H2  | Personal EWMA baseline > population      | EXP-AB-001  | Calibration error       |
| H3  | Explainability increases trust           | EXP-XAI-003 | Trust uplift ≥ +10%     |
| H4  | Adaptive features stable under drift     | EXP-004     | Drift resilience index  |
| H5  | Governance loops reduce degraded periods | EXP-GOV-004 | Degraded cycle duration |

Source:

- docs/research/02-scientific-hypotheses.md
- docs/grant/06-methodology.md
- docs/grant/07-experimental-design.md
- docs/grant/12-statistics.md
- docs/research/11-rd-technical-dossier.md §7, §8, §9

## 1.4 Algorithm Specification and Numerical Evidence

Key verified formulas (source: production code):

- riskScore = 0.55 × P_pred + 0.25 × P_anomaly + 0.20 × sigmoid(zScore)
- Burnout Index = weighted sum of 6 normalised factors (weights: 30/20/20/10/15/5)
- ML Trust = clamp([0.40 acc + 0.25(1−cal) + 0.20(1−drift) + 0.15 cov] × samplePenalty)

Numerical proof examples (team BI=55, individual riskScore=0.780) in dossier §5.

Source:

- docs/grant/appendices/A03-metrics-calculation-sheet.md
- docs/research/11-rd-technical-dossier.md §2, §5

## 1.5 Evidence and Traceability

Source:

- docs/research/01-traceability-matrix.md
- docs/grant/30-reproducibility.md
- docs/research/11-rd-technical-dossier.md §10

## Horizon Europe References

- EIC Work Programme 2026: https://eic.ec.europa.eu/eic-funding-opportunities/eic-pathfinder_en
- Funding and Tenders Portal (application process): https://research-and-innovation.ec.europa.eu/funding/how-apply/application-process_en
- EIC Pathfinder FAQ (eligibility and conditions): https://eic.ec.europa.eu/eic-frequently-asked-questions/faqs-general-conditions-and-eligibility_en
- Evaluation Form (expert criteria): https://ec.europa.eu/info/funding-tenders/opportunities/docs/2021-2027/horizon/temp-form/ef/ef_he-eic-pathfinder-open_en.pdf
- Advice for Applicants: https://rea.ec.europa.eu/guidance/advice-applicants_en
