# Lead → Paid Pipeline

One pipeline, used identically in Jobber (request/quote/job/invoice stages) and the
Google Sheet lead tracker (`tracking/lead-tracker-template.csv`). The Sheet's `Status`
column uses exactly these values so the dashboard formulas work.

## Statuses (in order)

| # | Status | Meaning / rule |
|---|---|---|
| 1 | **New Lead** | Untouched. SLA: contact within 15 min during work hours |
| 2 | **Contacted** | Spoke, or left voicemail + text |
| 3 | **Waiting on Customer** | They owe you info / photos / a decision |
| 4 | **Needs Site Visit** | Can't quote from photos |
| 5 | **Quote Needed** | Info complete, quote not yet sent |
| 6 | **Quote Sent** | Record amount + date the moment it goes out |
| 7 | **Follow-Up Needed** | Quote aging; a follow-up date is set |
| 8 | **Won / Scheduled** | Job date set |
| 9 | **Job Completed** | Work done, walk-through passed |
| 10 | **Invoice Sent** | |
| 11 | **Paid** | Terminal — success |
| 12 | **Lost** | Terminal — lost reason REQUIRED |
| 13 | **Dead / Bad Fit** | Terminal — spam, out of area, wrong service |

## Fields tracked on every lead

- **Attribution:** Lead source (Facebook / Website / Google / Referral / Repeat / Other) •
  Campaign name • Ad name • Form source (Meta instant form vs. website form)
- **Contact:** Name • Phone • Email • Address/town
- **Job:** Service type • Project size (acres or description) • Vegetation/difficulty note
- **Money:** Quote amount • Final invoice amount • Estimated cost (from the calculator) •
  Gross profit (invoice − estimated cost; update with actual hours/fuel after the job)
- **Dates:** Lead date • Quote sent date • Follow-up date • Close date • Job date •
  Invoice date • Paid date
- **Outcome:** Lost reason (Price / Went with competitor / Ghosted / DIY / Postponed /
  Out of area / Bad fit) • Notes

## Working rules that keep the data honest

- Update every touched lead's status **the same day** — a 2-minute evening habit.
- `Ghosted` is not `Lost on price` — they get different re-marketing later.
- Phone-call leads bypass tracking unless you ask **"how'd you find me?"** and log it.
  Skip this and the dashboard undercounts Facebook — you'll kill ads that were working.
- Every `Lost — Price` lead gets one message 60–90 days later (the brush grew back on
  whoever they hired, or they never did it).
