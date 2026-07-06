# System Stack Decision

## The decision: KEEP JOBBER (Core plan)

Verified July 2026: Jobber Core is $39/mo billed monthly, **~$28–29/mo billed annually**.
Core natively covers the entire lead→quote→job→invoice→paid pipeline, unlimited
quotes/invoices, scheduling, an **embeddable website request form**, and **instant push
notifications to your phone** when a request comes in. No alternative at ≤$30/mo does
all of that.

**Billing:** staying on monthly ($39) for now — the annual switch (~$10/mo saved) is
deferred until the next couple of jobs land and cash flow allows the upfront annual charge.

## Options compared

| Option | Cost/mo | Quoting/Invoicing | Meta lead sync | SMS/notify | Setup | Maintenance | Reporting | Fit |
|---|---|---|---|---|---|---|---|---|
| **A. Jobber Core only** | ~$29 (annual) + $17–20 routing | ✅ Native | ❌ needs Zapier/LeadSync | App push native; SMS via router | Low (you know it) | Low | Basic; weak on ad attribution & profit | Good but blind on "which ad paid" |
| **B. Jobber Core + Google Sheets dashboard (RECOMMENDED)** | ~$29 + ~$20 Zapier ≈ **$49** | ✅ Jobber | ✅ Zapier → Jobber + Sheet | SMS by Zapier + Jobber push | Medium (one-time) | Low (15 min/wk) | ✅ Full attribution + profit (Sheet) | **Best** |
| C. Google Forms/Sheets only | $0–20 | ❌ none — you'd lose quoting/invoicing/scheduling | Via Zapier | Hard — free email-to-SMS gateways are dead (AT&T 6/2025, T-Mobile 12/2024, Verizon dying 3/2027) | Medium | Medium (everything manual) | DIY | Downgrade — saves $29, costs hours |
| D. Switch CRM (Bigin $7–12, HubSpot Free, GHL $97) | $0–97 | Bigin: ❌ (needs Zoho Invoice bolt-on) · HubSpot: ❌ invoicing not free · GHL: ✅ | Bigin: ✅ native · HubSpot: ✅ native · GHL: ✅ | Only GHL has real SMS | High (rebuild everything) | Medium | Mixed | GHL is 3× budget; others lose invoicing. **No clear win → don't switch** |

## Recommended stack (Option B) — total ~$75–90/mo all-in (drops ~$10 after the annual Jobber switch)

| Piece | Tool | Cost | Why it's needed |
|---|---|---|---|
| CRM / quotes / invoices / schedule | **Jobber Core** | $39/mo now (monthly); ~$29/mo once switched to annual | Already yours; does the whole job pipeline natively |
| Meta lead sync + SMS + Sheet logging | **Zapier Professional (annual)** | ~$20/mo | FB Lead Ads is a premium Zapier app (paid plan required). One hub runs everything: Meta lead → Jobber request + Sheet row + SMS. 750 tasks/mo ≈ 200+ leads/mo of headroom |
| Lead tracker + pricing calculator + dashboard | **Google Sheets** | $0 | Jobber Core's reporting can't answer "which ad produced paid, profitable work" — one Sheet does |
| Website | Simple builder (Squarespace/Wix/WordPress) that allows embed code | ~$15–30/mo | Landing pages for ads, trust, SEO; hosts the Jobber request form + privacy policy (required by Meta lead ads) |
| Ads | Meta | $750/mo ($25/day — confirmed budget) | The lead source |

## Cheaper variant

If ~$49/mo software feels heavy: replace Zapier with **LeadSync** ($16–19/mo —
purpose-built Meta→SMS+Jobber delivery in under 60 seconds, SMS $5/100) and hand-enter
leads into the Sheet weekly (~15 min). Loses the automation, saves ~$5–10/mo. Zapier is
recommended because the automatic Sheet row is what makes the reporting real.

## Rejected for cause

- **Meta Business Suite free push notifications** — reported 15-minute-to-hours delays;
  fails the "respond in minutes" requirement.
- **Make.com** (~$11/mo) — cheaper than Zapier but fiddlier; fine as a DIY alternative
  if you enjoy tinkering.
- **Privyr free app** — great instant push on Meta leads, but doesn't write to Jobber or
  Sheets. Keep in your back pocket as an emergency backup notifier.
- **GoHighLevel** ($97/mo) — 3× budget, agency-grade complexity for a one-man shop.
