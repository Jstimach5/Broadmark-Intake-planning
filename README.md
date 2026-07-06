# Broadmark Forestry Mulching — Lead Generation & Sales Tracking System

A simple, bulletproof inbound lead system for Broadmark, a one-person forestry mulching
business in southeast Michigan (Cat 275XE + HM418): **Meta ads + website → instant SMS
to your phone → tracked through quote → job → invoice → paid**, with reporting that
shows which ads create *paid, profitable* work — not just leads.

> All prices, benchmarks, and cost figures were verified via web research in July 2026,
> then calibrated with the owner's confirmed numbers (loan, goal, local comps, budget) —
> see [Confirmed facts](#confirmed-facts) below.

## The system in one paragraph

**Keep Jobber. Add a ~$20/mo routing layer and one Google Sheet. Run one consolidated
Meta campaign. Price off a rate card with a $1,200 minimum.** Jobber Core keeps quoting,
invoicing, and scheduling. Zapier Professional (~$20/mo) syncs Meta lead-ads into
Jobber, logs every lead with its campaign + ad name to a Google Sheet, and texts your
phone within a minute (carrier confirmed Verizon — the default SMS path works). The
website's quote form is Jobber's own embeddable request form — zero middleware. One
Google Sheet holds the lead tracker, the quote calculator, and the dashboard that tells
you whether the month covered the ~$3,750 equipment payment.

## Monthly cost

| Piece | Tool | Cost/mo |
|---|---|---|
| CRM / quotes / invoices / schedule | Jobber Core | $39 now (monthly billing); switch to annual ~$29 after the next couple jobs land |
| Meta lead sync + SMS + Sheet logging | Zapier Professional (annual) | ~$20 |
| Lead tracker + calculator + dashboard | Google Sheets | $0 |
| Website (builder tier that allows embed code) | Squarespace / Wix / WordPress | ~$15–30 |
| Ads | Meta | $750 ($25/day — confirmed budget) |

## Repo map

| Path | What it is |
|---|---|
| [`checklist.md`](checklist.md) | **Start here** — the phased build checklist (must-have vs. later) |
| [`docs/system-stack.md`](docs/system-stack.md) | The CRM decision and full stack comparison (Options A–D) |
| [`docs/lead-routing-setup.md`](docs/lead-routing-setup.md) | Step-by-step Zap configuration, SMS plan, reliability ritual |
| [`docs/pipeline.md`](docs/pipeline.md) | Pipeline statuses and the fields tracked on every lead |
| [`website/site-structure.md`](website/site-structure.md) | Pages and homepage section-by-section layout |
| [`website/homepage-copy.md`](website/homepage-copy.md) | Build-ready homepage copy (fill in the bracketed placeholders) |
| [`website/quote-form-fields.md`](website/quote-form-fields.md) | Quote form fields — website long form + Meta instant short form |
| [`ads/campaign-plan.md`](ads/campaign-plan.md) | Campaign structure, budgets, targeting, tracking, seasonality |
| [`ads/ad-copy.md`](ads/ad-copy.md) | Six complete ad angles with headlines, primary text, and targeting |
| [`ads/shot-list.md`](ads/shot-list.md) | The 14-shot photo/video list with where each is used |
| [`pricing/rate-card.md`](pricing/rate-card.md) | Rate card, surcharges, add-ons, discount rules, red flags |
| [`pricing/calculator-spec.md`](pricing/calculator-spec.md) | Quote calculator formulas and how to import the template |
| [`pricing/calculator-template.csv`](pricing/calculator-template.csv) | Import into Google Sheets — working calculator with formulas |
| [`tracking/lead-tracker-template.csv`](tracking/lead-tracker-template.csv) | Import into Google Sheets — the lead tracker columns |
| [`tracking/dashboard-spec.md`](tracking/dashboard-spec.md) | Dashboard blocks A–D and the monthly targets |
| [`playbooks/follow-up-scripts.md`](playbooks/follow-up-scripts.md) | First-response SMS, call script, follow-up cadence, objections |
| [`playbooks/weekly-review.md`](playbooks/weekly-review.md) | The weekly 10-min, monthly 30-min, and quarterly rituals |

## The money math that drives everything

Calibrated to the confirmed numbers: **$3,7XX/mo payment (0% loan, ~$202k remaining)**
and the **$10,000/mo revenue goal within a 25-mile radius** (~5–6 full days ≈ 45–48
machine-hours/month).

- Loan allocation at the target utilization: $3,750 ÷ ~46 hrs ≈ **$80 per machine-hour**
  (it falls as you book more hours — see `pricing/calculator-spec.md`).
- Cash operating cost (fuel, teeth, maintenance, insurance at the confirmed $400/mo,
  truck, your wage) ≈ **$89/hr** → all-in ≈ **$165–175/hr** at target utilization.
  Walk-away floor: **$190/hr effective**.
- A typical full-day job ($1,800 + $150 mobilization) throws off ≈ **$1,250 gross
  profit** → the payment is covered by **~3 full-day jobs (~27 machine-hours)** per month.
- At the $10k goal: gross profit ≈ $6,100/mo → **payment coverage ≈ 1.6×** (the 2.0×
  stretch target = ~$12.5k/mo).
- **Ad budget reality check:** $750/mo ÷ ~$40/lead ≈ 18 leads → at ~15% lead-to-job ≈
  **2–3 jobs ≈ $5–6k/mo from paid ads** — roughly half the goal. The other half comes
  from Google Business Profile (free), referrals, repeat/maintenance work, and the
  existing Facebook audience. Scale the ad budget only after coverage holds ≥1.5 for two
  straight months.
- Ads are judged monthly on **cost per WON job**, never cost per lead.

## Confirmed facts

| # | Question | Answer |
|---|---|---|
| 1 | Phone carrier | **Verizon** → SMS by Zapier works as designed (T-Mobile was the only blocker) |
| 2 | Base + radius | **36440 Northline Rd, Romulus MI** / Judd & Rawsonville Rd, **Sumpter Twp** — 25-mile radius, SE Michigan |
| 3 | Loan | **$3,7XX/mo exact, ~$202k remaining, 60-month 0% interest** (~54 payments left) |
| 4 | Goal | **$10,000/mo in work**, all local |
| 5 | Local comps | Estimated **$1,800–3,000 per 8-hr day** → rate card anchored to the bottom of that range |
| 6 | Creative | Photos/videos exist on the Facebook page + Google Photos |
| 7 | Name | **Broadmark** is the customer-facing name |
| 9 | Ad budget | **$25/day** (~$750/mo) |
| 10 | Sales tax | Not needed now |
| — | Jobber annual billing | **Deferred** until a couple more jobs land; staying monthly ($39) for now |

## Still open (each sharpens a number — none block the build)

1. **Exact loan payment digits** ($3,7XX) — enter into the calculator and dashboard.
2. ~~Insurance~~ — **CONFIRMED: $400/mo ($4,800/yr)**. All "insured" claims on the site
   and in ads are cleared to publish. Cost is baked into the calculator at ~$9/machine-hour.
3. **Domain** — e.g. `broadmarkmulching.com`; check availability at website build.
