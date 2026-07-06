# Lead Routing & SMS Notification Setup

**Design principle: two independent channels for every lead** — one SMS, one app push —
so a single point of failure never costs a lead. This matters because **Meta deletes lead
data after 90 days**: a silent sync failure is unrecoverable.

## The flow (target: SMS on your phone < 1 minute after submission)

```
Meta ad (instant form)  ─┐
                          ├─→ Lead lands in Jobber + Sheet with source, campaign, ad name
Website quote form      ─┘        │
                                  ├─→ SMS/push to your phone (name, phone, service, size, town)
                                  ├─→ Status = New Lead, follow-up task created
                                  └─→ Auto-reply to customer: "Got it — I'll call you shortly."
You call/text within 5–15 min → statuses advance through the pipeline
```

## Zap 1 — Meta leads (Zapier Professional)

1. **Trigger:** Facebook Lead Ads → *New Lead* (instant). Connect the Facebook account
   that admins the business page; select the page and the lead form.
2. **Action 1:** Jobber → *Create Request*. Map name, phone, email (if collected), and
   put service / size / timeline / city into the request details.
3. **Action 2:** Google Sheets → *Create Spreadsheet Row* in the lead tracker. Map every
   column, including the Meta metadata fields Zapier exposes: **`campaign_name`,
   `ad_name`, `adset_name`, `form_id`** — this is what makes ad attribution automatic.
   Set `Lead Source = Facebook`, `Form Source = Meta instant form`, `Status = New Lead`.
4. **Action 3:** SMS by Zapier → *Send SMS* to your verified number:

   ```
   NEW LEAD (FB/{{ad_name}}): {{name}} {{phone}} — {{service}}, {{size}}, {{city}}, {{timeline}}
   ```

## Zap 2 — Website leads

1. **Trigger:** Jobber → *New Request* (fires when someone submits the embedded website
   request form).
2. **Action 1:** Google Sheets → *Create Spreadsheet Row*. `Lead Source = Website`,
   `Form Source = Website form`, `Status = New Lead`.
3. **Action 2:** SMS by Zapier → same message format, prefixed `NEW LEAD (Website)`.

> Zap 2's trigger also fires for requests Zap 1 creates. Add a Zapier **Filter** step
> after the trigger: continue only if the request source/details do NOT contain the
> marker Zap 1 writes (e.g. include "via Facebook" in Zap 1's request details and filter
> it out here). Verify during setup.

## Backup channel (free, automatic)

Jobber's mobile app **push notification** fires the moment a request is created — for
website submissions natively, and for Meta leads when Zap 1 creates the request.

> ⚠ **Verify during setup** that Zapier-created requests trigger the push. If they
> don't, install Privyr's free app (native Meta lead ads connection, instant push) as
> the backup channel for Meta leads.

## SMS by Zapier — caveats (verified July 2026)

- **Carrier check: RESOLVED.** SMS by Zapier doesn't work on T-Mobile-network phones —
  the owner's carrier is confirmed **Verizon**, which is fully supported, so the default
  path above works as designed. (If the carrier ever changes to T-Mobile, swap the SMS
  steps for LeadSync ($16–19/mo, SMS $5/100) or a ClickSend step (~$0.03/msg + one-time
  sole-prop A2P registration).)
- 153-character limit (the message format above fits), 15 msgs/hour cap (fine at this
  volume), US-only, one-way.

## Customer-side instant response (speed-to-lead without robo-texting)

- Meta instant form **thank-you screen** + Jobber's automatic request confirmation email:
  "Got it — I'll call you shortly."
- Your actual first text goes from **your own phone** (see
  `playbooks/follow-up-scripts.md`) — personal, compliant, and no A2P registration is
  needed for person-to-person texting.

## Reliability ritual (5 min/month — non-negotiable)

1. Submit a test lead through **Meta's Lead Ads Testing Tool** → confirm all three fire:
   SMS + Jobber request + Sheet row.
2. Zapier's Facebook connection is documented to **fail silently** when the token expires
   or page permissions change. Turn ON Zapier error emails, AND compare the Meta Leads
   Center lead count vs. the Sheet count monthly.
3. After any Facebook password change or page permission change: reconnect the
   Zapier↔Facebook connection immediately.
