# Broadmark Forestry Mulching — Lead Generation & Sales Tracking System

A simple, bulletproof inbound lead system for a one-person forestry mulching business
(Cat 275XE + HM418): **Meta ads + website → instant SMS to your phone → tracked through
quote → job → invoice → paid**, with reporting that shows which ads create *paid,
profitable* work — not just leads.

> All prices, benchmarks, and cost figures were verified via web research in July 2026.
> Estimates and assumptions are flagged inline where they appear; see
> [Questions to confirm](#questions-to-confirm-before-going-live) below.

## The system in one paragraph

**Keep Jobber. Add a ~$20/mo routing layer and one Google Sheet. Run one consolidated
Meta campaign. Price off a rate card with a $1,200 minimum.** Jobber Core (switched to
annual billing, ~$29/mo) keeps quoting, invoicing, and scheduling. Zapier Professional
(~$20/mo) syncs Meta lead-ads into Jobber, logs every lead with its campaign + ad name
to a Google Sheet, and texts your phone within a minute. The website's quote form is
Jobber's own embeddable request form — zero middleware. One Google Sheet holds the lead
tracker, the quote calculator, and the dashboard that tells you whether the month
covered the ~$4,400 equipment payment.

## Monthly cost

| Piece | Tool | Cost/mo |
|---|---|---|
| CRM / quotes / invoices / schedule | Jobber Core (annual billing) | ~$29 |
| Meta lead sync + SMS + Sheet logging | Zapier Professional (annual) | ~$20 |
| Lead tracker + calculator + dashboard | Google Sheets | $0 |
| Website (builder tier that allows embed code) | Squarespace / Wix / WordPress | ~$15–30 |
| Ads | Meta | $600–900 to start |

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

- All-in cost ≈ **$135–155 per machine-hour** *including* your wage and the loan →
  $150/hr revenue is break-even; **$200+/hr is the healthy floor**.
- Loan payment ≈ **$4,400/mo** ($220k @ 7–9%, 60 mo — confirm your actual rate/term) ≈
  **~32 billable machine-hours or ~4–5 typical jobs per month** to cover it.
- Ads are judged monthly on **cost per WON job**, never cost per lead.

## Questions to confirm before going live

None of these block the build — assumptions are labeled where used — but each sharpens a number:

1. **Phone carrier?** SMS by Zapier does not work on T-Mobile (fallback documented in `docs/lead-routing-setup.md`).
2. **Base location + real service radius?** Sets ad geo, travel tiers, seasonality, and the local rate tier.
3. **Exact loan rate and term?** Payment estimated at $4,356–4,567/mo (7–9%, 60 mo).
4. **Current and target billable machine-hours per month?** Cost allocation assumes ~83/mo.
5. **What do local competitors charge?** Calibrate the rate card with 2–3 real comps.
6. **What photos/videos exist today?** Determines whether ads launch week 4 or need 1–2 jobs shot first.
7. **Is "Broadmark" the customer-facing name? Existing domain / Google Business Profile / Facebook page?**
8. **Current insurance coverage and annual cost?** Feeds the calculator's $/hr.
9. **Ad budget comfort?** Plan assumes $600–900/mo; below ~$450/mo the data is too slow to learn from.
10. **Your state's sales-tax treatment of land-clearing services?** Affects quoting language and Jobber invoice setup.
