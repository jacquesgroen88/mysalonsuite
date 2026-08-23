# New Client Onboarding Playbook — GHL Lead & Member System

How to stand up the salon-suite (or similar) automation for a new client in a new GoHighLevel sub-account. Built from the My Salon Suite Minnesota build. This is a repeatable SOP.

## The model
**Build the system once, clone it forever. Authenticate each client's domain once.**

There are two layers, and they scale differently:

| Layer | Scales how | Repeat per new client? |
|---|---|---|
| **System** — workflows, email templates, calendars, tags, custom values | Clone via GHL **Snapshot** | No rebuild. Clone in minutes. |
| **Domain auth** — email sending domain + booking domain | Tied to the client's own domain + external DNS | Yes, once per sub-account (~5 min + their IT) |

Reminder on terminology: a GHL **sub-account** is called a **"Location"** in GHL. A client's multiple physical sites (e.g. 6 salons) live inside **one** sub-account as tags. You do **not** repeat setup per physical site, only per sub-account (i.e. per new client/operator).

---

## What carries in a Snapshot (build once)
Save the MSS build as a snapshot; these clone into every new sub-account:
- All workflows (with email steps linked to templates — this is why we link templates properly now)
- All email templates (`MSS - NN` set + member emails)
- Calendars (structure)
- Custom fields, custom values, tags
- Pipelines / opportunity stages

## What does NOT carry (redo per client, ~30 min total)
- **Email sending domain + DNS** (client's own domain — see checklist below)
- **Booking domain + DNS** (client's own domain)
- **A2P 10DLC** SMS brand + campaign registration (per sub-account, days to approve — start first)
- **Phone number** provisioning
- **Google calendar connection** (each manager connects their own Google)
- **Landing page** (lives on Netlify, cloned separately) + booking-widget embed
- **Business profile** (name, address for email footer)
- Client-specific content in custom values (location name, address, manager, booking link)

---

## Step-by-step for each new client

1. **Create the sub-account** in the GHL agency (or client provides access).
2. **Load the snapshot** → clones the whole system (workflows, emails, calendars, fields, tags).
3. **Start the two slow items immediately** (they have approval/propagation delay):
   - A2P 10DLC registration (Settings → Phone Numbers).
   - Email sending domain DNS (below) — client IT adds records.
4. **Customize client data** — set the custom values for their location(s): name, address, Facebook URL, manager name/phone/email, profit-calculator/review links, booking link.
5. **Build + connect the calendar**, have each manager connect their Google (two-way sync).
6. **Landing page** — clone the LP, swap branding/photos/copy, embed the client's booking widget, deploy.
7. **Verify template links** — confirm each workflow email step uses "Select existing template" (the snapshot should preserve this if the master was built correctly).
8. **Compliance** — set business mailing address; unsubscribe is automatic.
9. **Test** — run a test contact end-to-end.
10. **Publish** — flip workflows Draft → Published only after DNS is verified and the test passes.

---

## Domain DNS checklist (reusable, `mg.` / `book.` convention)

Always use the same subdomain prefixes on the **client's** root domain, so it's the identical checklist every time.

### A. Email sending domain — `mg.<clientdomain>`
GHL: **Settings → Email Services → Dedicated Domains → Create/Add Domain** → enter `mg.<clientdomain>` → **Add & Verify** → **Continue** → it generates these 5 records (Mailgun):

| Type | Host | Value | Priority |
|---|---|---|---|
| TXT (SPF) | `mg` | `v=spf1 include:mailgun.org ~all` | — |
| TXT (DKIM) | `mx._domainkey.mg` | `k=rsa; p=…` (copy the unique key from GHL) | — |
| CNAME | `email.mg` | `mailgun.org` | — |
| MX | `mg` | `mxa.mailgun.org` | 10 |
| MX | `mg` | `mxb.mailgun.org` | 10 |

Send these to the client's IT. **Do not click Verify in GHL until the records are live** (then it auto-verifies). Set the default From Name/Email on that domain.

### B. Booking domain — `book.<clientdomain>` (recommended, hides GHL from prospects)
GHL: **Settings → Domains → Add Domain** → `book.<clientdomain>` → it provides a **CNAME target** → client IT adds the CNAME → verify.

---

## Time per new client (after the snapshot exists)
- System (snapshot clone + customize): ~1 hour.
- Domain auth: ~5 min of our clicks + client IT + propagation.
- A2P: minutes to submit, days to approve (start day 1).
- Template-link check + test + publish: ~30 min.

The heavy build only ever happens once. Everything after is this checklist.
