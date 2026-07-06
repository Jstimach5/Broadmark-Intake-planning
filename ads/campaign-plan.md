# Meta Ad Campaign Plan

## Benchmarks to plan against (verified mid-2026)

- Forestry mulching Facebook cost per lead: **$30–50** (niche agency data); land clearing
  broadly $20–80; plan on **$35–75 per raw lead** in a rural market.
- Tree-service analogs: ~11% lead-to-job; one case study: ~$12K spend → 57 jobs,
  $130.9K revenue in 120 days.
- Instant forms convert cheaper (20–30% lower CPL) but close worse than website leads
  (website leads close ~2–3×) — **niche agencies still recommend instant forms as
  primary** for rural mobile users; manage quality via form questions + fast follow-up,
  not landing-page friction.
- Meta lead data is only retrievable for **90 days** — the CRM sync must exist from day one.

## Structure (2026 consensus: consolidate — don't fragment)

At small budgets, many campaigns = none of them learn. The 6 "campaigns" in
[`ad-copy.md`](ad-copy.md) are **ad angles**, deployed as creatives inside ONE
consolidated campaign and rotated seasonally:

- **Campaign 1 — "Leads – Core" (always on):** Leads objective → Instant Form. One ad
  set: radius targeting (30–50 mi or a county list matching real drive time),
  **"People living in this location"**, broad age 28–65+, Advantage+ audience with
  interest *suggestions* (hunting, rural living, tractor/land brands) — not hard
  filters. **3–5 ads live at once**, drawn from the angles (start: Reclaim + Fence Line
  + Mulching-vs-Dozer; swap in Hunting Prep Jul–Sep).
- **Campaign 2 — "Retargeting" (month 2+, after pixel/audiences accumulate):** the
  credibility angle. Audiences: 50%+ video viewers, page engagers, site visitors
  30–60 days; **exclude** submitted leads. $3–5/day.
- **Website landing-page variant (test in month 2–3):** duplicate the best instant-form
  ad but send it to the matching service page. Costs more per lead, closes better —
  decide with cost-per-WON-job data, not CPL.

## Budget

- **Start: $20–30/day** on Campaign 1 (~$600–900/mo → expect ~10–25 leads/mo at
  benchmark CPL). Below $15/day the data is too slow to learn from.
- Judge nothing before **2 weeks or ~$300–500 spent**; avoid edits that reset learning
  (budget swings >20%, creative/targeting changes).
- Kill/scale rule: after ~5 leads per ad, kill the worst, clone the best with a new
  hook. Monthly, decide on **cost per WON job**, never on CPL alone.
- Seasonality: budget up Feb–Aug; hunting-prep creative Jul–Sep; expect the worst CPL
  Nov–Jan — cut to a $5–10/day retargeting ember or pause, and pre-book winter work in
  the fall.

## Instant form setup

- Fields (short version — see `website/quote-form-fields.md`): Name, Phone, City,
  Service, Approx. size, Timeline.
- Start with **"More volume"** form type; switch to **"Higher intent"** (adds a review
  screen) if the junk rate is high.
- **Privacy policy URL is mandatory** to publish a form → one-page policy on the website.
- Auto-message on submit: "Thanks [Name] — I'll call you shortly from [number]. Text
  photos of the area to speed up your quote."

## Tracking & naming (do this BEFORE first publish — names freeze into UTMs at publish)

- Names carry attribution end-to-end: campaign `FM-Leads-Core`, ads
  `BA-Timelapse-15s-v1`, `FenceLine-Track-v1`, `HuntPrep-Lanes-v1`, …
- The Zapier sync receives **`campaign_name`, `ad_name`, `adset_name`, `form_id`** plus
  the form answers — this fills the lead tracker's attribution columns automatically.
- Website links from ads get the UTM template:
  `utm_source=facebook&utm_medium=paid_social&utm_campaign={{campaign.name}}&utm_content={{ad.name}}`
- Install the Meta pixel on the website day one (retargeting audiences + Lead event on
  the form thank-you); add a partner Conversions API integration if the site builder
  offers one-click (Meta reports 17.8% lower cost per result vs. pixel-only).

## Compliance notes

- No special ad category applies to land services — but avoid **"financing available"**
  wording (Credit trigger) and **"get your lot ready to sell"** framing (Housing
  trigger); either can get the ad auto-restricted and strip targeting precision.

## Creative rules (what verifiably performs in this niche)

- **Before/after in the first 3 seconds** — the niche's proven hook; a 15s before/after
  timelapse reportedly outperforms static images 3–5×.
- 15–30s, shot vertical 9:16, raw phone footage (UGC-style outperforms polished in
  2026), burned-in captions (most feed video plays muted).
- Structure every video: 0–3s hook (machine hits brush / whip-pan before-after) →
  3–15s transformation + service area → CTA "Get a free quote".
