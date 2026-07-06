# Quote Calculator — Spec & Import Instructions

The working template is [`calculator-template.csv`](calculator-template.csv). It becomes
Tab 2 ("Calculator") of the Google Sheet.

## How to import

1. Open the Google Sheet → **File → Import → Upload** → choose the CSV.
2. Import location: **Insert new sheet(s)**.
3. **Check "Convert text to numbers, dates, and formulas"** — this is what turns the
   `=...` cells into live formulas.
4. Format cell B37 (Gross profit %) and B39 (payment share) as **Percent**.
5. Optional polish: bold the section header rows, fill the INPUT value cells (B5–B9,
   B12–B21, B24–B27) light yellow, and add conditional formatting to turn B42/B43 red
   when they contain "RED".

## How it works

- **Inputs (edit per quote):** machine hours, travel time, distance, difficulty
  multiplier, mobilization.
- **Cost settings (review quarterly):** fuel burn/price, tooth wear, maintenance, wage,
  insurance, loan $/hr, truck $/mile, target margin, monthly payment.
- **Computed:**
  - *Direct cash cost* = machine hrs × (fuel + teeth + maintenance + wage + insurance)
    + travel hrs × wage + round-trip miles × truck $/mile
  - *Full cost* = direct cash cost + machine hrs × loan $/hr
  - *Cost-plus quote* = full cost × (1 + target margin)
  - *Rate-card quote* = best-fit tier from the hours (3-hr hourly ≤3 h → half-day ≤4.5 h
    → full day ≤8.5 h → multi-day) × difficulty multiplier + mobilization
  - **QUOTE = the HIGHER of cost-plus vs. rate-card** — never quote below either
  - *Gross profit*, *GP%*, *effective $/machine-hr*, and *share of the monthly equipment
    payment this job covers*
- **Sanity flags:** effective rate below $175/hr → RED; gross profit under 25% → RED.
  If either is red, re-scope or walk away — see the discount rules in
  [`rate-card.md`](rate-card.md).

## Loan allocation note

The default `Loan allocation = $53/hr` assumes ~1,000 billable machine-hours/yr
(~83/mo) against a ~$4,400/mo payment. If you're running fewer billable hours, raise it
(e.g., at 40 hrs/mo the true allocation is ~$110/hr) — otherwise "profitable" quotes
quietly stop covering the payment.

## After each job

Enter the *actual* hours and fuel back into the lead tracker's `Estimated Cost` /
`Gross Profit` columns so the dashboard reports real profit, not estimates.
