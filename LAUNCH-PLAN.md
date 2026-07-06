# Broadmark Properties — Launch Plan (Implementation Runbook)

> **For the implementing agent/session:** this document is self-contained. The full
> system design lives in this repo (`jstimach5/broadmark-intake-planning`, branch
> `claude/forestry-lead-generation-planning-7ahx7r`). Everything below is sequenced —
> do the phases in order, because later phases have hard dependencies on earlier ones
> (Meta will not publish a lead form without the live privacy-policy URL from Phase A).

## What this system is

Owner-operated forestry mulching business (Broadmark Properties, Sumpter Township MI,
Cat 275XE + HM418). Lead flow: **Meta ads + website → Jobber CRM + Google Sheet →
instant SMS to the owner's phone → tracked lead → quote → job → invoice → paid**, with
a dashboard that shows which ads create profitable work and whether the month covered
the ~$3,7XX equipment payment.

## What already exists (do not rebuild)

| Asset | Where | State |
|---|---|---|
| Complete static website (10 pages, brand-styled, real job photos, privacy policy) | `website/site/` | Built; needs deploy + 3 placeholders filled |
| Ad campaign plan, 6 ad angles with copy, naming conventions | `ads/campaign-plan.md`, `ads/ad-copy.md` | Final |
| Two finished ad creatives (verified: owner's real photos only) | Canva — square: `canva.com/d/PWJeu7x_piDjUkw` · vertical 9:16: `canva.com/d/GKPAscDaXD9bvq5` | Vertical approved & export-ready; square needs the real phone number in its CTA line |
| Photo library (7 committed web-ready; catalog + gap list) | `assets/photos/`, `ads/creative-library.md` | 14 more photos pending from owner |
| Rate card, quote calculator (importable CSV with formulas) | `pricing/` | Final; insurance $400/mo confirmed at $9/hr |
| Lead tracker template (CSV) + dashboard spec | `tracking/` | Final |
| Lead routing design (2 Zaps) + SMS plan | `docs/lead-routing-setup.md` | Designed; not yet configured |
| Pipeline statuses/fields, stack decision | `docs/pipeline.md`, `docs/system-stack.md` | Final |
| Follow-up scripts, weekly/monthly rituals | `playbooks/` | Final |

## Confirmed business facts (use these; do not re-ask)

- Carrier **Verizon** → SMS by Zapier works. Ad budget **$25/day**. Insurance
  **$400/mo, confirmed** — "Licensed & Insured" claims are cleared everywhere.
- Loan: **0% interest, ~$3,7XX/mo, ~$202k remaining** → owner must supply exact digits.
- Goal: **$10,000/mo**, all within ~25 miles of Sumpter Twp (Judd Rd & Rawsonville Rd).
- Rate card: $250/hr (3-hr min) · $1,000 half-day · $1,800 full-day · $1,700/day
  multi-day · $1,200 minimum · $150 mobilization · walk-away floor $190/hr effective.
- Brand: sage `#617455`, cream `#F2EDC9`, black `#20241C`, serif "BROADMARK PROPERTIES".

## ⚠ Standing rules for the implementing agent

1. **Real job photos ONLY in all creative — never AI-generated or stock imagery,
   especially equipment.** If generating designs, audit every image fill afterward.
2. Never quote or publish prices other than the rate card without owner approval.
3. Anything that spends money (domain purchase, Zapier plan, ad budget activation)
   or requires account login/OAuth is an **owner action** — prepare it, hand it off,
   verify after.
4. Do not launch ads until the Phase D end-to-end test passes (otherwise leads strand
   inside Meta, unnotified, and are deleted after 90 days).

## Owner inputs needed (collect once, at the start)

- [ ] Business phone number (replaces `[PHONE]` everywhere)
- [ ] Business email (privacy page + form notifications)
- [ ] Exact monthly loan payment ($3,7XX)
- [ ] Domain choice (suggest `broadmarkmulching.com` / `broadmarkproperties.com`; ~$12/yr)
- [ ] Logo PNG file (exists; currently only shared as an inline image)
- [ ] Logins available for: GitHub/Netlify, Jobber, Google, Zapier, Meta Business, Canva

---

## Phase A — Website live (blocks everything Meta-related)

1. In `website/site/`: find-and-replace `[PHONE]` (visible text) and `tel:+15555555555`
   (links) with the real number; fill `[DATE]`/`[EMAIL]` in `privacy.html`; add the
   owner's 2–3 personal sentences on `about.html` where marked.
2. Add the logo (once the PNG lands): header img (~40px tall next to the wordmark),
   hero above the H1, `<link rel="icon">` favicon.
3. In Jobber: Settings → Requests → configure the form with the fields in
   `website/quote-form-fields.md` → copy the "Add to your website" embed code → paste
   into the marked SETUP NOTE boxes in `index.html` and `quote.html` (delete the notes).
4. Deploy: **owner drags the `website/site/` folder onto app.netlify.com → "Deploy
   manually"** (free). Connect the purchased domain in Netlify domain settings.
5. Verify: every page loads on the live URL; tap-to-call works on a phone; the Jobber
   form submits and the owner gets Jobber's push notification + email;
   `https://<domain>/privacy.html` resolves (write this URL down — Phase C needs it).

## Phase B — Google Sheet (the tracker, calculator, and dashboard)

1. Create one Google Sheet named **"Broadmark Leads & Money"**. Import
   `tracking/lead-tracker-template.csv` as tab **Leads** and
   `pricing/calculator-template.csv` as tab **Calculator** (File → Import → *check
   "Convert text to numbers, dates, and formulas"*). Delete the example lead row.
2. Calculator tab: enter the exact $3,7XX payment in the "Monthly equipment payment"
   cell; sanity-check an 8-hr job quotes **$1,950** with all flags OK.
3. Add data-validation dropdowns on Leads: `Status` (13 values in `docs/pipeline.md`),
   `Lead Source`, `Lost Reason`.
4. Build tab **Dashboard** per `tracking/dashboard-spec.md` (blocks A–D, COUNTIFS/
   SUMIFS over Leads, monthly targets: revenue $10,000, GP ~$6,100, ~3 jobs to cover
   the payment, ad-spend entry cells per campaign).
5. Verify: add one fake lead row → every dashboard block updates; then delete it.

## Phase C — Meta foundation (form + pixel, no spend yet)

1. Meta Business Suite: confirm the Broadmark Facebook page is tidy (logo as profile
   image, cover photo from `assets/photos/`, phone + live website URL filled in).
2. Events Manager: create a **Meta pixel**, paste its base code before `</head>` on all
   10 site pages, redeploy, verify with Meta's pixel helper. Add a `Lead` event on the
   quote form thank-you.
3. Ads Manager → Instant Form: build per `ads/campaign-plan.md` — fields Name, Phone,
   City, Service (multiple choice), Approx. size, Timeline; type **More volume**;
   **privacy policy URL from Phase A** (mandatory); thank-you message: "Thanks — I'll
   call you shortly from [number]. Text photos of the area to speed up your quote."
4. Do NOT create the campaign yet.

## Phase D — Lead routing (Zapier) + the go/no-go test

1. Owner subscribes to **Zapier Professional** (~$20/mo annual — Facebook Lead Ads is
   a premium app; the free plan cannot do this).
2. Build **Zap 1** (Meta → everything) and **Zap 2** (website/Jobber → Sheet + SMS)
   exactly per `docs/lead-routing-setup.md`, including the loop-prevention filter on
   Zap 2 and the SMS message format. Map Meta's `campaign_name` / `ad_name` fields
   into the Sheet's attribution columns.
3. Turn ON Zapier error-notification emails.
4. **Go/no-go test:** submit a test lead via Meta's Lead Ads Testing Tool AND one real
   submission through the live website form. PASS = each produces, within ~1 minute:
   SMS on the owner's phone + Jobber request + correctly-attributed Sheet row.
   Do not proceed until both pass.

## Phase E — Launch ads

1. Export creatives from Canva (Share → Download → JPG): the vertical
   (`canva.com/d/GKPAscDaXD9bvq5`) and the square (`canva.com/d/PWJeu7x_piDjUkw` —
   first put the real phone number in its CTA text line).
2. Ads Manager, exactly per `ads/campaign-plan.md`: campaign **FM-Leads-Core**, Leads
   objective → the Phase C instant form; one ad set, **25-mile radius pin at Judd Rd &
   Rawsonville Rd, Sumpter Twp**, "People living in this location", broad 28–65+,
   Advantage+ with interest *suggestions* only (hunting, rural living, tractor/land
   brands); **$25/day**.
3. Three ads to start (copy verbatim from `ads/ad-copy.md`): `BA-Reclaim-Sq-v1`,
   `BA-Reclaim-Story-v1`, and a single-image variant using
   `assets/photos/BA-woods-02-after-a.jpg` with the Mulching-vs-Dozer copy
   (`MulchVsDozer-Img-v1`). Name everything BEFORE publishing — names freeze into
   tracking at first publish.
4. Owner reviews and clicks publish (it's their ad account and card).
5. Same week (free, high value): create the **Google Business Profile** — it feeds
   reviews and is the #2 lead source in this niche.

## Phase F — Operations (what "running" means)

- **Speed-to-lead:** SMS reply within 15 min during work hours (templates in
  `playbooks/follow-up-scripts.md`, saved as phone text shortcuts); every quote through
  Jobber; every touched lead's Sheet status updated same evening (2 min).
- **Follow-up cadence:** day 2–3 text, day 7 call, day 14 last text, day 30 → Lost
  (reason required — it feeds the dashboard).
- **Weekly 10 min / monthly 30 min** reviews per `playbooks/weekly-review.md`. The
  monthly review includes the **reliability ritual**: test lead through Meta's testing
  tool + compare Meta Leads Center count vs. Sheet count (Zapier's Facebook connection
  is documented to fail silently).
- **Ad decisions monthly, on cost per WON job** (never cost per lead), min 5 leads per
  ad before judging. Kill worst, clone best. Scale past $25/day only after the
  payment-coverage gauge holds ≥1.5 for two straight months.
- **Content habit:** every job produces 1 before/after pair + 1 vertical clip (shot
  list and gaps in `ads/shot-list.md` / `ads/creative-library.md`; a 30–60s tripod
  timelapse is the #1 missing asset).

## Deferred / nice-to-have (do not block launch)

- Remaining 14 curated photos from the owner → fill catalog, unlock the hunting/
  fence-line/trails ad angles (list and batches in `ads/creative-library.md`)
- Retargeting campaign at month 2 (audiences need time to accumulate)
- Landing-page ad variant test at month 2–3; partner Conversions API
- Switch Jobber billing monthly → annual (~$10/mo saved) once cash flow allows
- Per-town SEO pages; review-request automation (month 3+)

## Success criteria (30 days after ads go live)

1. Every lead produced an SMS within 1 minute and a correctly-attributed Sheet row.
2. ≥15 leads, ≥60% contacted within 15 min (per Sheet timestamps vs. lead dates).
3. Dashboard answers, without manual work: leads by ad, cost per lead, cost per WON
   job, gross profit by job type, payment-coverage gauge.
4. At least 2 jobs won from ads (benchmark: ~11–15% lead-to-job at $35–75/lead).
