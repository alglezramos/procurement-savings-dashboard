# Procurement Savings Program Control Tower

Interactive dashboard to govern a portfolio of procurement savings projects, built from the point of view of a **Procurement Program Manager / Transformation Office**.

**Live demo:** https://alglezramos.github.io/procurement-savings-dashboard/

> All data is fictitious and for demonstration only. Figures in EUR thousands. UI available in English and Spanish.

## What it shows

| View | Content |
|---|---|
| **Overview** | KPIs with month-over-month deltas (annualised target, pipeline forecast, risk-adjusted, **FY landing vs full-year plan**, realized YTD vs in-year plan, value at risk, project health), realization S-curve vs plan, **target-to-commitment bridge (waterfall)**, **savings quality by type and Finance validation**, pipeline by stage-gate, savings by category, owner scorecard, top risks, auto-generated insights (incl. stalled projects) |
| **Portfolio** | Sortable project register: owner, category, lever, **savings type**, stage, **days in stage (aging)**, confidence, target / forecast / risk-adjusted / realized, RAG health, Finance validation. Click a row for the project drawer |
| **Risks** | 5×5 probability × impact heat map (clickable) and risk register with probability %, impact, EMV, owner, mitigation and status |
| **Timeline** | Gantt with sticky project names, FY / full-horizon range toggle, stage colour, P&L start milestone, today line, tooltips. Jump here from any project ("Show on timeline") |
| **Process & method** | Stage-gate flow (L0 Idea → L5 Realizing, gates G1–G5, re-scope loop) with live counts, savings definitions and a worked example (forecast → risk-adjusted → downside) |

Filters, language and timeline range are kept in the URL, so a link reproduces the exact view. **Export CSV** downloads the filtered portfolio (or the risk register on the Risks tab); **Print / PDF** prints the current view.

## Savings methodology (summary)

- **Baseline**: last 12 months' price × forecast volume, agreed before the sourcing event.
- **Savings types**: cost reduction (hard, EBITDA) · cost avoidance (reported, not in budget baseline) · working capital (valued at financing cost, below EBITDA).
- **Stage confidence**: L0 10% · L1 25% · L2 50% · L3 70% · L4 90% · L5 100%.
- **Risk-adjusted savings** = forecast × stage confidence (the number committed to the CFO).
- **Value at risk (EMV)** = Σ probability × impact of open and mitigating risks.
- **Downside case** = risk-adjusted − open-risk EMV (conservative stress view, not the commitment).
- **FY landing** = realized to date + Nov–Dec at confidence-weighted run-rate, vs full-year P&L plan.
- **Stage aging**: days in current stage vs a healthy maximum (L0 45 · L1 60 · L2 90 · L3 90 · L4 60); >1.5× = stalled.
- **MoM deltas**: every KPI vs the snapshot frozen at the previous month-end.
- **Realized** = (baseline price − actual PO price) × actual volume, validated monthly by Finance.
- **Health (RAG)**: at risk if forecast < 80% of target or EMV > 25% of forecast; watch if < 90% or EMV > 12%.

## Tech

Single self-contained `index.html` (HTML + CSS + vanilla JS, SVG charts, no build step, no dependencies). To use real data, edit the `P` (projects, incl. `ty` savings type, `sd` stage-entry date and `pv` previous-month snapshot), `R` (risks), `PLAN` and `PROGRAM_TARGET` constants at the top of the script, or replace them with a fetch from a CSV/JSON export of the savings tracker.

## Author

Alejandro González Ramos — Procurement & Supply Chain · MSc Supply Chain Management, ZLC (MIT SCALE Network)
