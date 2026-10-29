# Procurement Savings Program Control Tower

Interactive dashboard to govern a portfolio of procurement savings projects, built from the point of view of a **Procurement Program Manager / Transformation Office**.

**Live demo:** enable GitHub Pages (Settings → Pages → Deploy from branch `main` / root) and open `https://<your-user>.github.io/procurement-savings-dashboard/`

> All data is fictitious and for demonstration only. Figures in EUR thousands. UI available in English and Spanish.

## What it shows

| View | Content |
|---|---|
| **Overview** | KPIs (annualised target, pipeline forecast, risk-adjusted savings, realized YTD vs in-year plan, value at risk, project health), realization S-curve vs plan, pipeline by stage-gate, savings by category, owner scorecard, top risks, auto-generated insights |
| **Portfolio** | Sortable project register: owner, category, lever, stage, confidence, target / forecast / risk-adjusted / realized, RAG health, Finance validation. Click a row for the project drawer |
| **Risks** | 5×5 probability × impact heat map (clickable) and risk register with probability %, impact, EMV, owner, mitigation and status |
| **Timeline** | Gantt of execution windows with stage colour, P&L start milestone and today line |
| **Process & method** | Stage-gate flow (L0 Idea → L5 Realizing, gates G1–G5, re-scope loop) with live counts, plus savings definitions |

## Savings methodology (summary)

- **Baseline**: last 12 months' price × forecast volume, agreed before the sourcing event.
- **Hard vs soft**: hard = P&L reduction vs baseline; soft = cost avoidance / working capital (reported separately).
- **Stage confidence**: L0 10% · L1 25% · L2 50% · L3 70% · L4 90% · L5 100%.
- **Risk-adjusted savings** = forecast × stage confidence (the number committed to the CFO).
- **Value at risk (EMV)** = Σ probability × impact of open and mitigating risks.
- **Realized** = (baseline price − actual PO price) × actual volume, validated monthly by Finance.
- **Health (RAG)**: at risk if forecast < 80% of target or EMV > 25% of forecast; watch if < 90% or EMV > 12%.

## Tech

Single self-contained `index.html` (HTML + CSS + vanilla JS, SVG charts, no build step, no dependencies). To use real data, edit the `P` (projects), `R` (risks), `PLAN` and `PROGRAM_TARGET` constants at the top of the script, or replace them with a fetch from a CSV/JSON export of the savings tracker.

## Author

Alejandro González Ramos — Procurement & Supply Chain · MSc Supply Chain Management, ZLC (MIT SCALE Network)
