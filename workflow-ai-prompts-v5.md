# MSS Blaine — GHL "Build using AI" Prompts (v5, clean template set)

Supersedes `workflow-ai-prompts.md` (which referenced the deleted MSS v1/v2 names).
How to use: GHL → Automation → Workflows → **+ New** → **Build using AI** (purple). Paste ONE prompt, review the scaffold, fix any step that didn't auto-match, **Save as Draft**, test, then publish.

Entry model: the LP "Book a Tour" uses the **calendar booking widget** (calendar `8jAyUAwUQ8e0RKEd3548`), so **booking the appointment is the trigger**. All template names below exist exactly as written. Sender = "My Salon Suite Blaine".

---

## SMS copy (paste where each prompt references Text #N)

- **Text #1 (confirmation):** Hi {{contact.first_name}}, it's {{custom_values.blaine__manager_name}} at My Salon Suite Blaine. Your tour is booked! See the details in your email. Reply here anytime with questions.
- **Text #2 (reminder):** Hi {{contact.first_name}}, quick reminder: your My Salon Suite Blaine tour is {{appointment.start_time}}. We're at {{custom_values.blaine__location_address}}. See you there! Reply if anything changes.
- **Text #2a (no-show / cancelled):** Hi {{contact.first_name}}, sorry we missed you! No problem at all. Grab a new time whenever it suits you: {{custom_values.blaine__booking_link}}
- **Text #2b (toured, no reservation):** Hi {{contact.first_name}}, great meeting you at My Salon Suite Blaine! Any questions about your suite or next steps? I'm here whenever you're ready to hold your spot.
- **Text #3 (member, 1 week in):** Hi {{contact.first_name}}, {{custom_values.blaine__manager_name}} here. You've been in your suite a week! How's it going? Anything you need, just reply.

---

## Workflow A — Tour Booked: Confirm & Prep
```
Create a workflow named "MSS Blaine - Tour Booked Confirm & Prep".
Trigger: a customer books an appointment on the "Blaine - Salon Suite Tour" calendar.
Steps in order:
1. Add tags "blaine leads" and "tour-booked".
2. Send an SMS: [paste Text #1].
3. Send the email template "MSS - 01 Tour Requested".
4. Create a task for the assigned user titled "Call new tour lead", due in 1 hour.
5. Wait until 1 day before the appointment start time.
6. Send the email template "MSS - 02 Tour Preparation".
7. Send an SMS: [paste Text #2].
Set sender name to "My Salon Suite Blaine". Save as draft.
```

## Workflow B — Tour Outcome Router
```
Create a workflow named "MSS Blaine - Tour Outcome".
Trigger 1: appointment status becomes "No Show" on the Blaine tour calendar -> add tag "tour-no-show".
Trigger 2: appointment status becomes "Cancelled" -> add tag "tour-cancelled".
After either, send an SMS: [paste Text #2a].
Save as draft.
```
Manual add after AI build: a branch (or 2nd workflow) where tag **toured-no-reservation** sends Text #2b + creates a manager follow-up task. "Showed" outcomes are tagged by the team: `toured-reservation` (signed/holding a suite) or `toured-no-reservation`.

## Workflow C — Lead Nurture / Evergreen / Reactivation
```
Create a workflow named "MSS Blaine - Lead Nurture".
Trigger: any of these tags is added: "tour-no-show", "tour-cancelled", "toured-no-reservation".
Stop/remove from workflow if tag "toured-reservation" or "lease-signed" is added.
Steps (send the email template, then wait the stated days):
Wait 2 days, send "MSS - 03 Profit Visualization".
Wait 2 days, send "MSS - 04 Brand Freedom".
Wait 2 days, send "MSS - 05 Lead Nurture Community".
Wait 2 days, send "MSS - 06 Profit Calculator".
Wait 5 days, send "MSS - 23 Member Tools and Savings".
Wait 6 days, send "MSS - 24 Product Partners and Revenue".
Wait 6 days, send "MSS - 25 Health Wellness and Protection".
Wait 6 days, send "MSS - 26 Community".
Wait 6 days, send "MSS - 09 Evergreen Security".
Wait 6 days, send "MSS - 10 Evergreen Decor".
Wait 6 days, send "MSS - 11 VIP Client Experience".
Wait 6 days, send "MSS - 12 Tax Benefits".
Wait 6 days, send "MSS - 16 Tech Stack".
Wait 6 days, send "MSS - 17 Education".
Wait 6 days, send "MSS - 18 All Pros".
Wait 6 days, send "MSS - 19 No Hidden Fees".
Wait 6 days, send "MSS - 20 Quiz".
Wait 6 days, send "MSS - 13 Final Push".
Wait 60 days, send "MSS - 21 Reactivation Timing".
Wait 30 days, send "MSS - 22 Reactivation What's New".
Set sender name to "My Salon Suite Blaine". Save as draft.
```

## Workflow D — Member Onboarding
```
Create a workflow named "MSS Blaine - Member Onboarding".
Trigger: tag "lease-signed" is added (also start if tag "toured-reservation" is added).
Steps:
1. Send the email template "Reservation & Application (Email 1)".
2. Wait 1 day, send "MSS - 00 Member Onboarding".
3. Wait 2 days, send "Meet Your Site Leader - Blaine".
4. Add tag "blaine members".
Set sender name to "My Salon Suite Blaine". Save as draft.
```

## Workflow E — Member Check-ins & Review
```
Create a workflow named "MSS Blaine - Member Check-ins".
Trigger: tag "lease-signed" is added.
Steps:
1. Wait 7 days, send an SMS: [paste Text #3].
2. Wait 21 days, send the email template "MSS - 14 Review Request".
3. Wait 56 days, send the email template "MSS - 15 Review Google".
Save as draft.
```
Deferred (Rachel "work on later"): Website Directory, Square Discount, Google Business member emails + monthly newsletters. Add to Workflow E once written.

---

## Notes / manual tweaks after AI scaffolds
- **Appointment-relative waits** (A step 5; reminder timing): if the AI uses a fixed wait, switch to **Wait → until a date/time relative to the appointment** (1 day before start). Rachel's exact rule: tour after 12pm = remind 9am same day; before 12pm = remind 6pm night before — set with two if/else branches on appointment hour if you want it exact.
- **SMS requires a phone number** on the account (Twilio port pending, ticket #27713407). Provision a GHL number for the pilot so SMS sends; emails work regardless.
- **Stop conditions**: in Workflow C, set the goal/stop event so a lead who signs exits the nurture immediately.
- After building, tell Claude and a test contact can be pushed through via API to trace the path.
