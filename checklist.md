# Build Checklist

**Legend: ▲ = must-have now · ○ = nice-to-have later**

## Phase 1 — Foundation (Week 1, mostly desk work)

- [ ] ▲ Answer the 10 questions in [`README.md`](README.md#questions-to-confirm-before-going-live) (carrier, loan terms, service radius, local comps)
- [ ] ▲ Positioning one-liner: "[Region]'s owner-operated forestry mulching — cleared in a day, no piles, no torn-up ground" (adjust to taste; used everywhere)
- [ ] ▲ Switch Jobber to annual billing (~$10/mo saved)
- [ ] ▲ Build the Google Sheet: Tab 1 lead tracker ([template](tracking/lead-tracker-template.csv)), Tab 2 quote calculator ([template](pricing/calculator-template.csv)), Tab 3 dashboard ([spec](tracking/dashboard-spec.md))
- [ ] ▲ Set your rate card numbers in the calculator; sanity-check against 2–3 local competitor quotes
- [ ] ▲ Configure the Jobber request form with the fields in [`website/quote-form-fields.md`](website/quote-form-fields.md)
- [ ] ○ Register/confirm domain + business email

## Phase 2 — Website (Weeks 2–3)

- [ ] ▲ Pick a builder tier that allows embed code; build the 10 pages ([structure](website/site-structure.md)) — homepage first, service pages can start as sections
- [ ] ▲ Embed the Jobber request form on Home + Quote Request pages; test a submission end-to-end (push + email arrive?)
- [ ] ▲ Publish the privacy policy page (Meta will not publish a lead form without it)
- [ ] ▲ Install the Meta pixel; set a Lead event on the form thank-you
- [ ] ○ Partner Conversions API integration if the builder offers one-click
- [ ] ▲ Load 6–10 best existing photos into the gallery (the [shot list](ads/shot-list.md) fills the rest as jobs happen)
- [ ] ○ Google Business Profile — free; a major second lead source in this niche and it feeds reviews

## Phase 3 — Ads (Week 4)

- [ ] ▲ Meta Business Manager + page tidy-up; verify admin access
- [ ] ▲ Build the instant form (fields + settings in [`ads/campaign-plan.md`](ads/campaign-plan.md): More Volume, privacy URL, auto-thank-you message)
- [ ] ▲ Create Zap 1 and Zap 2 ([setup guide](docs/lead-routing-setup.md)); send a test lead via Meta's Lead Ads Testing Tool; confirm SMS + Jobber request + Sheet row
- [ ] ▲ Name campaigns/ads per the convention in the campaign plan (names freeze into tracking at first publish)
- [ ] ▲ Launch Campaign 1 with 3 ads (Reclaim before/after, Fence line, Mulching-vs-dozer) at $20–30/day
- [ ] ○ Retargeting campaign (month 2, once audiences exist)
- [ ] ○ Landing-page variant test (month 2–3)

## Phase 4 — Lead handling (live from first ad day)

- [ ] ▲ Save the [follow-up scripts](playbooks/follow-up-scripts.md) as phone text templates
- [ ] ▲ Working rule: SMS reply within 15 min during work hours (cab breaks); calls returned at next break; the auto-acknowledgment covers the gap
- [ ] ▲ Every quote through Jobber (approval tracking); every lead's status updated same day in the Sheet (2-min evening habit)
- [ ] ▲ Follow-up cadence set as Jobber reminders: day 2–3, day 7, day 14
- [ ] ○ Photo release line + concealed-hazards line added to Jobber quote terms

## Phase 5 — Tracking & optimization (Week 6 onward)

- [ ] ▲ Weekly 10-min review ([ritual](playbooks/weekly-review.md)): dashboard blocks A+B, overdue follow-ups, this week's before/afters shot?
- [ ] ▲ Monthly 30-min review: full dashboard; kill worst ad / clone best (min 5 leads before judging); enter ad spend; run the reliability ritual
- [ ] ▲ Quarterly: reprice against actuals (fuel, tooth life, close rates); adjust the rate card
- [ ] ○ Month 3+: seasonal creative rotation (hunting prep Jul–Sep), review-request automation, per-town SEO pages
