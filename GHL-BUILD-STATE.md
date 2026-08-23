# MSS GHL Build State — Blaine Pilot

**Account:** My Salon Suite of Minnesota (single shared sub-account, all 6 locations)
**Location ID:** `3ZMk2Pl6YHHWQGk4AjEd`
**API key:** in gitignored `create-custom-fields.ps1` (PIT key, never commit/graph)
**API base:** `https://services.leadconnectorhq.com` · Version header `2021-07-28`
**Architecture note:** ONE account serves all locations. Location is a segment (tags `blaine leads`/`blaine members`, etc.), NOT a separate sub-account. Workflows branch by location tag; per-location merge data lives in `{location} - ...` custom values.

---

## Phase 0 — Data layer ✅ DONE (2026-06-29)

### Custom values created (merge as `{{custom_values.<name>}}`)
| Name | Value | ID |
|---|---|---|
| Blaine - Location Name | Blaine | C5XjaZxOK9yo1OWmBkgL |
| Blaine - Location Address | 1341 113th Ave NE, Blaine, MN 55434 | v8qidG3HIeDtQcylFdoF |
| Blaine - Facebook URL | https://www.facebook.com/mysalonsuiteblaine | 848CadQL554fIfG3QGmn |
| Blaine - Manager Name | Stacey Cleveland | WQ67i19K0PaH1kzBjiFs |
| Blaine - Manager Phone | 612-429-6360 | hkqPj69vtugzXTMwTnhJ |
| Blaine - Manager Email | scleveland@mysalonsuite.com | eSQNMfLohgZWuTKfgllF |
| Blaine - Booking Link | PENDING (set to Stacey GHL calendar link after Step 3) | VsrnseKiW6OQ4kC6LVzg |
| Profit Calculator URL | https://www.mysalonsuite.com/profit-calculator/ | pQ2g10goGc3I8jI9d84j |

### Lifecycle / branch tags created
| Tag | ID |
|---|---|
| tour-requested | mx4TqWvthY6mOtiRQMWA |
| tour-booked | fK7KG8YM3P5lmO9XboMr |
| tour-no-show | tclewTYsEy2kGKUfPL1Y |
| tour-cancelled | P0x0RdGmnqoiNTYY0IRQ |
| toured-no-reservation | i7478Kt14SFD3PH0WtQZ |
| toured-reservation | T9wDI1ZO5T8IBVBWsXs3 |
| lease-signed | nyMzLQ08sdGw2jqpbG2g |

Pre-existing useful tags: `blaine leads`, `blaine members`, `mss leads`, `mss members`, `follow-up`, `warm lead`, `opted out`.
Pre-existing custom fields: `contact.preferred_time`, `contact.calendly_url` (unused now), `contact.guide_link`, `contact.google_review_link`.

---

## Step 3 — Calendar ✅ DONE (2026-06-29)
- Blaine tour calendar built in GHL by Jacques (assigned to himself for now; reassign to Stacey at team onboarding — does not affect workflows).
- Calendar ID: `8jAyUAwUQ8e0RKEd3548`
- Booking link: `https://api.leadconnectorhq.com/widget/booking/8jAyUAwUQ8e0RKEd3548` → written into `Blaine - Booking Link` custom value (merge `{{ custom_values.blaine__booking_link }}`).
- Tour date/time flows to emails/SMS via `{{appointment.start_time}}` (kills the 3 "where do we pull the time" questions).

## Step 6 — Email templates ✅ DONE (2026-06-29)
Deleted 44 old templates, created 27 correctly-named shells (`MSS - 00 … 26`), kept 11 member emails, then **set the HTML body of all 27 via API and verified the rendered content** (real HTML + `{{contact.first_name}}` etc., no default boilerplate).

**⚠️ CONTENT-SETTING METHOD (critical — do NOT regress):** the email HTML body is set by **`PATCH /emails/builder/{id}`** with body `{ locationId, editorType: "html", editorContent: "<html...>", name, subjectLine, fromName }`. The fields are **`editorType` + `editorContent`** — NOT `type`/`html` (those are silently ignored on create, leaving the default "Welcome to email" starter). The create POST only makes an empty shell; content always comes from this PATCH. Proven by `bulk-update-content.ps1`; scratchpad `fix_content.ps1` patched all 27. Paste-ready source files (merge tags converted) also at `email\ghl-ready\`.

**Retained member emails (already built, use as-is):** `Meet Your Site Leader - {6 locations}`, `Reservation & Application (Email 1)`, `Lease & Documents (Email 2)`, `Onboarding (Email 3) AV`, `Happy Birthday`, `Happy Anniversary`.

**Merge-tag map for workflow/email building:**
- `{{contact.first_name}}` · `{{contact.phone}}` · `{{contact.preferred_time}}`
- `{{appointment.start_time}}` (tour date/time, from calendar)
- `{{custom_values.blaine__booking_link}}` (calendar link)
- `{{custom_values.profit_calculator_url}}` (the renamed "guide")
- `{{contact.google_review_link}}`
- `{{custom_values.blaine__location_address}}` · `{{custom_values.blaine__manager_name}}` · `_phone` · `_email` · `blaine__facebook_url`

---

## Remaining (owner)
- **Step 4** Book-a-Tour form (NONE exists yet) + map Preferred Tour Time — You (UI)
- **Step 5** Embed form on Blaine v5 LP — You
- **Step 7** Workflow A (tour request) — You
- **Step 8** 4 tour-outcome branches — You
- **Step 9** Workflow B (nurture/evergreen/reactivation) — You
- **Step 10** Lead SMS + GHL number — You
- **Step 11** Workflow C (member onboarding) — You (member emails already exist)
- **Step 12** Workflow D (member check-ins) — You
- **Test + publish** — Claude (API test contact) + You

SMS/call gated by Twilio port (ticket #27713407) — provision GHL number to avoid blocking. UPDATE: a live number **+1 612-230-3554** is on the account, so SMS can send.

---

## Workflow audit (2026-07-01, via API + browser)

**Template names confirmed:** exactly `MSS - 00 … 26` (no "v5"). 

**Workflow inventory (by created date):**
- **Real A–E (built Jun 29 PM, drafts):** `Tour Booking Confirmation Workflow` (A), `Tour Outcome Automation` (B), `Lead Nurture Email Sequence` (C), `Blaine Member Onboarding` (D), `Member Check-in & Review` (E).
- **Stale leftovers (Jun 10, built against now-deleted old templates → DELETE):** `Tour Form Submission Sequence`, `Post-Tour No Booking Nurture`.
- **Snapshot defaults (Feb 27 → junk, delete/ignore):** numbered `1.`–`9.`, `License Renewals`, `MSS Members Birthday/Anniversary Text`.

**Workflow A structure = CORRECT:** trigger = customer books appointment on "Blaine - Salon Suite Tour" calendar → add Blaine lead tags → Tour Confirmation SMS → Tour Confirmation Email → create call task → wait until 1 day before appt → Tour Preparation Email → Tour Reminder SMS → End.

**⚠️ SYSTEMIC ISSUE FOUND:** the AI "Build using AI" created every email step as **"Quick compose"** (AI-written plain text) instead of **"Select existing template" → MSS - NN**. So the branded v5 HTML was NOT being sent. Fix per email node: open node → Create email → "Select existing template" → search + pick the `MSS - NN` → Save action → Save workflow.

**FIXED (2026-07-01, browser):** Workflow A — `Send Tour Confirmation Email` → `MSS - 01`, `Send Tour Preparation Email` → `MSS - 02`. Saved. (These are the only launch-critical emails.)

**REMAINING email-linking (Quick compose → template):**
- **C Lead Nurture:** MSS-03,04,05,06, 23,24,25,26, 09,10,11,12, 16,17,18,19,20,13, 21,22 (in sequence order; match by each step's Action Name).
- **D Member Onboarding:** `Reservation & Application (Email 1)`, `MSS - 00`, `Meet Your Site Leader - Blaine`.
- **E Member Check-ins:** `MSS - 14`, `MSS - 15` (+ Text #3 SMS).
- **B Tour Outcome:** mostly SMS; check for any email.
- Also: set **From Name = "My Salon Suite Blaine"** on email steps (currently blank → uses account default).
- Then **delete** the 2 stale Jun-10 workflows + snapshot junk.

Browser note: GHL builder deep-links render blank (open from the list); the tab renderer is very heavy (screenshots time out ~50%). Each node fix ≈ 8–10 laggy clicks.

---

## Domains / DNS

> **CORRECTION 2026-08-19 (verified live in the GHL UI).** The claim below that both domains were
> "provisioned in the MSS sub-account" is **WRONG**. Settings -> Email Services shows **no dedicated
> sending domain on the account at all**: the default provider is the shared `LeadConnector Email
> System (send.lcmsgsndr.org)`, and GHL displays its "you are using a shared sending domain" prompt.
> `mg.mysalonsuite.com` does not exist on the platform side. The DKIM key captured on 1 Jul came from
> a creation flow that was never completed, so the records sent to Rachel could never have verified
> even if MSS IT had added them. **Superseded by the `mail.mysalonsuite.com` decision (19 Aug):**
> create the sending domain fresh as `mail.`, capture the new DKIM, then reissue the IT sheet
> (`comms/MSS-DNS-EXPLAINER.html`). The old `comms/MSS-IT-DNS-REQUEST.*` files are DEAD, do not send.

> **SUPERSEDED 2026-08-23 — label changed `mail` -> `mn` at Rachel's request.** `mysalonsuite.com` is the
> **national franchisor domain**; MSS Minnesota is a 6-location regional operator. Rachel flagged that asking
> corporate to hand over `mail.` reads as one region claiming the brand's mail subdomain and would invite
> pushback. She is right, and it is a political constraint the earlier label decision missed entirely.
> **New label: `mn.mysalonsuite.com`** (free, verified 23 Aug). Records below keep their VALUES; only the
> host column changes (`mn`, `k1._domainkey.mn`, `email.mn`) and **the DKIM key is reissued again** because
> it is generated per subdomain. The `mail.mysalonsuite.com` entry in GHL is unused and should be deleted.
> **The `mail.` key below is DEAD — do not send it.** Rachel also offered to loop Jacques in on the email to
> corporate IT, which was accepted.

### CURRENT — `mn.mysalonsuite.com` (created 2026-08-23, pending client DNS)

Label chosen after Rachel flagged that `mysalonsuite.com` is the **national franchisor domain** and a generic
`mail.` would read as one region claiming the brand's mail subdomain. `mn` is regionally scoped, free, and
gives corporate a pattern other regions could reuse. **Do NOT click "Verify records" in GHL until the client's
DNS is live** — check propagation externally first.

| # | Type | Host | Value | Pri |
|---|---|---|---|---|
| 1 | TXT (SPF) | `mn` | `v=spf1 include:spf.leadconnectorhq.com include:mailgun.org ~all` | - |
| 2 | TXT (DKIM) | `pic._domainkey.mn` | `k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCgEBv1S1iAN1xXrB/rdNfRfjAICXJzf6gcVfB3GGm6nnSXY6YPiPXpQekKJQNbO2+fqbThWsc5YpO1Nl3FBnOOTskij+gM6qCG+0c2zzJvWh3nMLBo2T7urMXi/Ekh42ZMqOp99QQE6MGeBjBVLRhPVOtH7H8NfhGCinF2bDIL8wIDAQAB` | - |
| 3 | CNAME | `email.mn` | `mailgun.org` | - |
| 4 | MX | `mn` | `mxa.mailgun.org` | 10 |
| 5 | MX | `mn` | `mxb.mailgun.org` | 10 |
| 6 | CNAME | `book` | `sites.ludicrous.cloud` | - |
| 7 | CNAME | `blaine` | `mysalonsuite.netlify.app` | - |

**THE DKIM SELECTOR IS ASSIGNED PER DOMAIN AND IS EFFECTIVELY RANDOM.** Three domains produced three different
selectors: `mg` -> `mx._domainkey`, `mail` -> `k1._domainkey`, `mn` -> `pic._domainkey`. Never assume, infer or
carry one forward; read it off the screen every time. Key validated as a well-formed 1024-bit RSA SPKI, and all
three keys confirmed distinct.

**Still to do in GHL:** delete the unused `mail.mysalonsuite.com` and `mg.` entries.

Client sheet: `comms/MSS-DNS-EXPLAINER.html` + `My Salon Suite - Email and Booking Domain Setup.pdf`
(DKIM verified to copy out of the rendered PDF uncorrupted and re-parse). Send draft:
`comms/RACHEL-DNS-SEND-2026-08-20.md`, needs updating for the `mn` change before sending.

### SUPERSEDED (created 2026-08-20 as `mail.`, never sent to IT)

**Sending domain `mail.mysalonsuite.com`** created fresh in GHL (Settings -> Email Services -> Dedicated
Domain -> Add new domain). Label chosen deliberately over Mailgun's default `mg`: it is free on their zone,
it is what shows in the visible From address, and MSS already run this exact pattern with `go.mysalonsuite.com`
-> Act-On. **Do NOT click "Verify records" in GHL until the client's DNS is live.**

| # | Type | Host | Value | Pri |
|---|---|---|---|---|
| 1 | TXT (SPF) | `mail` | `v=spf1 include:spf.leadconnectorhq.com include:mailgun.org ~all` | - |
| 2 | TXT (DKIM) | `k1._domainkey.mail` | `k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDC1mEX20Bvv0ZlW3OqCcUiXFzabNHRFKaLzuwFpfW5ppn24WHGvZDZ3rbBTK3afPA+vuapQ9hVbG1QKFpnRr+/DkKhzMKDaHt0kAF4S6QulUs2mpIZpWBKh1YAKT47KvrVacwSael0e1E3/fWWtyb7JP1i+E3TDYXqEYLWxKg0gQIDAQAB` | - |
| 3 | CNAME | `email.mail` | `mailgun.org` | - |
| 4 | MX | `mail` | `mxa.mailgun.org` | 10 |
| 5 | MX | `mail` | `mxb.mailgun.org` | 10 |

**Three things changed vs the dead 1 Jul sheet, not one:** the label (`mg` -> `mail`), the **DKIM selector
(`mx` -> `k1`)**, and the key itself (regenerated, verified as a valid 1024-bit RSA SPKI). Any one of them
alone would have failed verification silently.

**Booking domain `book.mysalonsuite.com`** unchanged: single CNAME to `sites.ludicrous.cloud`. Optional.

**Client-facing doc:** `comms/MSS-DNS-EXPLAINER.html` + `comms/My Salon Suite - Email and Booking Domain Setup.pdf`.
The DKIM sits in a full-width copy block, NOT in the records table: inside the narrow table column the base64
wrapped and interleaved with neighbouring cells, so anyone copying it out of the PDF would have got a corrupted
string. Verified by extracting from the rendered PDF, stripping whitespace and re-parsing the key.

*(Historical, as written 2026-07-01:)* Both provisioned in the MSS sub-account, records generated, awaiting MSS IT to add them to `mysalonsuite.com`. **Do not click Verify in GHL until DNS is live.** Convention for future clients: `mg.` (email) + `book.` (booking) on the client's own domain.

**Email sending domain `mg.mysalonsuite.com`** (Settings → Email Services → Dedicated Domains):
| # | Type | Host | Value | Pri |
|---|---|---|---|---|
| 1 | TXT (SPF) | mg | v=spf1 include:spf.leadconnectorhq.com include:mailgun.org ~all | — |
| 2 | TXT (DKIM) | mx._domainkey.mg | k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDtfntBR5GPGyoLdBGGiSMPse2Q7/ijPLJFiGR5C7UPox+3mhv/QIhK7IWXAmYWQSTYIndotNZLZ2/MS0bP/P3yQdlQ0bQUvVGtHYEiqdj10Jt6fpYPRTDmTpxgGjbuWVzYlQPj4vwEpaOup+d5tU+HT6dmQy+HqIc7efK4VzB9ewIDAQAB | — |
| 3 | CNAME | email.mg | mailgun.org | — |
| 4 | MX | mg | mxa.mailgun.org | 10 |
| 5 | MX | mg | mxb.mailgun.org | 10 |

**Booking domain `book.mysalonsuite.com`** (Settings → Domains & URL Redirects → Funnel/Website):
| # | Type | Host | Value |
|---|---|---|---|
| 6 | CNAME | book | sites.ludicrous.cloud |

Full client-facing version in `comms/MSS-IT-DNS-REQUEST.md`. Only value not auto-captured: the DKIM `p=` key (tooling blocks key-like strings) — one-click copy from the GHL Dedicated Domains screen.
