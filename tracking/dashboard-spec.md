# Dashboard / Reporting Spec

**One dashboard tab, four blocks, updated by formulas from the lead tracker — no manual
report-building.** Weekly look (10 min): blocks A+B. Monthly look (30 min): all four.
All formulas aggregate the lead tracker tab (`lead-tracker-template.csv` columns) with
COUNTIFS/SUMIFS filtered by month and by the exact Status values in
[`docs/pipeline.md`](../docs/pipeline.md).

## Monthly targets (displayed at the top)

- Revenue target ($)
- Gross profit target ($)
- **Jobs needed to cover the equipment payment** = $4,400 ÷ average gross profit per job
  — starts at ~4–5 jobs and self-corrects as real data accumulates.

## Block A — Lead flow (this month + last 3)

- Leads by source (Facebook / Website / Google / Referral / Repeat)
- Leads by campaign and by ad name (Facebook only — filled automatically by the Zap)
- Cost per lead by campaign = ad spend (entered monthly, one cell per campaign) ÷ leads
- Junk/bad-fit rate by campaign (Dead ÷ total) — catches campaigns that "perform" on
  cost per lead but send garbage

## Block B — Sales conversion

- Quotes sent (count) • Quote rate (quotes ÷ contactable leads)
- Close rate (Won ÷ quotes sent) • Average quote $ • Average invoice $
- Quote→close lag (days) • Open follow-ups overdue (an action list, not a metric)

## Block C — Money & profit

- Revenue by job type • Gross profit by job type (invoice − estimated cost from the
  calculator; refined with actual hours/fuel after each job)
- **Gross profit per machine-hour by job type — the king metric: it tells you what to
  advertise more**
- Lost reasons breakdown
- **Equipment coverage gauge:** monthly gross profit ÷ monthly equipment payment
  (~$4,400 — confirm actual). Needs ≥ 1.0 before owner pay; target ≥ 2.0. Rule of thumb:
  the payment = ~32 machine-hours or ~3–5 typical jobs per month.

## Block D — Ad decisions (monthly)

- **Cost per WON job by campaign** (not per lead) = spend ÷ jobs won — the only number
  that decides ad budget
- Revenue per $1 of ad spend by campaign
- Best ad / worst ad (by cost per won job, minimum 5 leads before judging)
- Action row: scale / keep / kill per campaign

## Build notes

- Keep one small "Ad Spend" input area on the dashboard tab: one row per campaign per
  month, entered from Meta Ads Manager at the monthly review.
- Add a data-validation dropdown on the tracker's `Status` column using the 13 pipeline
  statuses, and on `Lead Source` and `Lost Reason` — clean values are what make every
  formula on this tab work.
