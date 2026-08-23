# My Salon Suite (Blaine) — Go-Live Setup Brief for Diane

**Client:** My Salon Suite of Minnesota (pilot = Blaine location)
**What this is:** An automated lead + member journey built in GoHighLevel (GHL). A stylist books a tour on the landing page → GHL fires confirmation + reminder emails/SMS → nurtures no-shows and non-bookers → onboards new members. This brief gets it ready to switch on.
**Your GHL account:** "My Salon Suite Minnesota" sub-account · Location ID `3ZMk2Pl6YHHWQGk4AjEd`
**This is an internal JCE brief** — GHL terminology is fine here (never use it in client-facing wording).

---

## Start the SMS registration FIRST (it has a long approval delay)

### 1. Email sending domain — already set up (Jacques is handling handover)
The dedicated sending domain `mg.mysalonsuite.com` is already created in GHL and the DNS records are generated. Jacques is coordinating the DNS with Rachel's IT directly. **Nothing for you to build here.** Once IT confirms the records are added, someone will click **Verify** in GHL (Settings → Email Services → Dedicated Domains) and set the default **From Name = "My Salon Suite Blaine"**. If Jacques asks you to grab the DKIM key: it is copied from that same Dedicated Domains screen.

### 2. A2P 10DLC registration (US SMS compliance)
US law requires registration before automated SMS will deliver.
- In GHL: **Settings → Phone Numbers → Trust Center / A2P 10DLC.** Complete **Brand registration** (business details) + **Campaign registration** (describe the use case: appointment reminders + lead follow-up).
- The account already has a live number: **+1 612-230-3554.**
- *Why first:* approval takes **several days to ~2 weeks.** Emails work without it, but SMS steps won't deliver until it's approved.

---

## Main task: link the email templates in the workflows

**Background:** the 5 workflows were built with GHL's "Build using AI." It created each email as **"Quick compose" (plain AI text) instead of using our branded templates.** Every email step must be repointed to its matching **`MSS - NN`** template (these hold the real designed HTML). Jacques/Claude already fixed **Workflow A** (the entry workflow) — you're doing C, D, and E.

### The fix procedure (same for every email step)
1. **Automation → Workflows →** open the workflow.
2. Click the **email step** (a green envelope node).
3. In the right panel, scroll down to **"Create email."** It will be set to **Quick compose.**
4. Click **"Select existing template."**
5. A search box appears → type the template number (e.g. `03`) → click the matching **`MSS - NN …`** result (it gets a blue check).
6. While you're there, set **From Name = "My Salon Suite Blaine"** (optional but do it).
7. Click **"Save action."**
8. Click **"Save"** (top-right) to save the workflow.
9. Repeat for every email step. (SMS steps and wait steps are fine — leave them.)

> Tip: each email node's **Action Name** tells you which one it is (e.g. "Send Profit Visualization Email" → pick `MSS - 03 Profit Visualization`). Match by meaning.

### Which template goes in which workflow

**Workflow C — "Lead Nurture Email Sequence"** (the big one, ~20 emails, in this order):
`MSS - 03 Profit Visualization` · `MSS - 04 Brand Freedom` · `MSS - 05 Lead Nurture Community` · `MSS - 06 Profit Calculator` · `MSS - 23 Member Tools and Savings` · `MSS - 24 Product Partners and Revenue` · `MSS - 25 Health Wellness and Protection` · `MSS - 26 Community` · `MSS - 09 Evergreen Security` · `MSS - 10 Evergreen Decor` · `MSS - 11 VIP Client Experience` · `MSS - 12 Tax Benefits` · `MSS - 16 Tech Stack` · `MSS - 17 Education` · `MSS - 18 All Pros` · `MSS - 19 No Hidden Fees` · `MSS - 20 Quiz` · `MSS - 13 Final Push` · `MSS - 21 Reactivation Timing` · `MSS - 22 Reactivation What's New`

**Workflow D — "Blaine Member Onboarding"** (3 emails):
`Reservation & Application (Email 1)` · `MSS - 00 Member Onboarding` · `Meet Your Site Leader - Blaine`

**Workflow E — "Member Check-in & Review"** (2 emails + 1 SMS):
`MSS - 14 Review Request` · `MSS - 15 Review Google` (leave the SMS/Text step as-is)

**Workflow B — "Tour Outcome Automation":** mostly SMS. Open it and if any email step is on "Quick compose," repoint it; otherwise nothing to do.

---

## Do NOT delete anything (Jacques handles all cleanup)

There are old and duplicate workflows in the account, but **please do not delete anything.** Jacques will clean those up himself. Your only job is to edit the workflows listed above. If you are ever unsure whether a workflow is one of yours, leave it alone.

**The only workflows you open and edit:**
- `Lead Nurture Email Sequence` (C)
- `Blaine Member Onboarding` (D)
- `Member Check-in & Review` (E)
- `Tour Outcome Automation` (B) — only if it has a Quick-compose email step

**Leave everything else exactly as it is** and do not delete, rename, or move it: `Tour Booking Confirmation Workflow` (already done), `Tour Form Submission Sequence`, `Post-Tour No Booking Nurture`, the numbered snapshot workflows, the `MSS Members` folder, and all templates.

---

## Confirm the calendar sync

- **Calendars →** open **"Blaine - Salon Suite Tour."**
- Confirm it's connected to a **Google account with two-way sync** (Connections tab): "check for conflicts" ON, and bookings write into a Google calendar.
- It's assigned to Jacques for now. When the MSS team is onboarded, reassign to **Stacey Cleveland** and connect *her* Google. (Nothing else changes.)

---

## Compliance (quick)

- **Settings → Business Profile:** make sure a **physical mailing address** is set (required in email footers / CAN-SPAM). GHL adds the unsubscribe link automatically.

---

## White-labeling (do before scaling to all 6 locations — not a pilot blocker)

Booking links currently show a `leadconnectorhq.com` URL. To brand them:
- **Settings → Domains:** add a custom domain like `book.mysalonsuite.com` (client DNS again) so booking/calendar links show MSS branding, not GoHighLevel.

---

## Final steps (Jacques + Claude will do / confirm)

- **Redeploy** the Blaine landing page to Netlify (the booking widget is already embedded).
- **Test:** Claude runs a test contact through Workflow A to confirm the chain fires with the right emails.
- **Publish:** flip each of the 5 workflows from **Draft → Published** — ONLY after emails are linked, the sending domain is verified, and the test passes.

---

## Who owns what

| Task | Owner |
|---|---|
| Email sending domain — created + records generated | Done (Jacques/Claude) |
| Email sending domain — add DNS + verify | Rachel / MSS IT, then Jacques |
| A2P 10DLC registration | Diane |
| Link templates in C/D/E + From Name | Diane |
| Clean up old / duplicate workflows | Jacques (not Diane) |
| Confirm calendar Google sync | Diane |
| Business address / compliance | Diane |
| Custom booking domain (later) | Diane + client DNS |
| Redeploy LP, test, publish | Jacques / Claude |

**When C, D, E are linked and cleanup is done, tell Jacques** so Claude can run the end-to-end test before publishing.

*Reference for Claude/Jacques: full technical state in `GHL-BUILD-STATE.md`; template source files in `email/ghl-ready/`.*
