# Broadmark Website — Launch Instructions

This folder is a complete, self-contained static website (10 pages, one stylesheet,
your real job photos). No builder subscription required — host it free.

## Before launch (15 minutes)

1. **Replace the phone number** — every page uses `[PHONE]` as visible text and
   `tel:+15555555555` in links. Find-and-replace both with your real number.
2. **Paste the Jobber form** — `index.html` and `quote.html` each contain a highlighted
   "SETUP NOTE" box. Replace it with your Jobber request-form embed code
   (Jobber → Settings → Requests → "Add to your website").
3. **Privacy page** — fill in `[DATE]` and `[EMAIL]` in `privacy.html`. This page's URL
   is what Meta requires before publishing lead forms.
4. **About page** — add 2–3 personal sentences and (ideally) a photo of you with the
   machine where marked.
5. **Meta pixel** — after creating it in Meta Events Manager, paste the pixel base code
   before `</head>` on every page.

## Hosting options (pick one)

- **Netlify (easiest, free):** app.netlify.com → "Deploy manually" → drag this whole
  `site` folder onto the page. Done — you get a live URL immediately; connect your
  domain in Site settings → Domain management.
- **GitHub Pages (free):** repo Settings → Pages → deploy from branch → point at this
  folder (or copy it to a `docs/` folder on the default branch).
- **Any builder later:** all copy lives in `../homepage-copy.md` and these pages —
  paste into Squarespace/Wix if you'd rather manage it visually.

## Domain

Buy `broadmarkmulching.com` (or similar) at any registrar (~$12/yr) and point it at
your host. Until then the free Netlify/Pages URL works fine for ads.

## Test after launch

Submit the quote form once → confirm the Jobber push notification and the Zapier SMS
both fire → check the row lands in the lead tracker Sheet.
