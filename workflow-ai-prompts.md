# MSS Blaine — "Build using AI" Prompts for GHL Workflows

How to use: In GHL, go to **Automation › Workflows › Build using AI** (purple button).
Paste ONE prompt per workflow. Review the generated steps, then adjust any template
picker that didn't auto-match, and Save as Draft. Test before publishing.

Template names referenced below are EXACTLY as they appear in Marketing › Emails.

---

## Workflow 1 — Tour Form Submitted (highest priority)

```
Create a workflow named "MSS - Tour Form Submitted".

Trigger: when a contact submits the "Book a Tour" form.

Steps in order:
1. Send the email template "MSS v2 - 01 Tour Requested".
2. Add the tag "tour-requested".
3. Wait 3 days.
4. Send the email template "MSS v1 - 03 Profit Visualization".
5. Wait 4 days.
6. Send the email template "MSS v1 - 04 Brand Freedom".
7. Wait 4 days.
8. Send the email template "MSS v1 - 05 Lead Nurture Community".

Set sender name to "My Salon Suite Blaine" and sender email to
"scleveland@mysalonsuite.com" for all emails. Save as draft.
```

---

## Workflow 2 — Tour Preparation (24h reminder)

```
Create a workflow named "MSS - Tour Preparation (24h)".

Trigger: when an appointment status changes to "Confirmed".

Steps in order:
1. Wait until 24 hours before the appointment start time.
2. Send the email template "MSS v2 - 02 Tour Preparation".

Set sender name to "My Salon Suite Blaine" and sender email to
"scleveland@mysalonsuite.com". Save as draft.
```

---

## Workflow 3 — Post-Tour, No Booking

```
Create a workflow named "MSS - Post-Tour No Booking".

Trigger: when an appointment status changes to "Completed".

Steps in order:
1. Wait 1 day.
2. If/Else condition: check whether the contact has the tag "lease-signed".
   - If the tag EXISTS: stop the workflow.
   - If the tag DOES NOT exist: continue with the steps below.
3. Send the email template "MSS v2 - 03 Profit Visualization".
4. Wait 4 days.
5. Send the email template "MSS v1 - 09 Evergreen Security".
6. Wait 5 days.
7. Send the email template "MSS v1 - 11 Evergreen Client Experience".
8. Wait 5 days.
9. Send the email template "MSS v1 - 13 Evergreen Final Push".

Set sender name to "My Salon Suite Blaine" and sender email to
"scleveland@mysalonsuite.com" for all emails. Save as draft.
```

---

## Workflow 4 — Member Onboarding

```
Create a workflow named "MSS - Member Onboarding".

Trigger: when the tag "lease-signed" is added to a contact.

Steps in order:
1. Send the email template "MSS v2 - 00 Member Onboarding".
2. Wait 7 days.
3. Send the email template "MSS v1 - 14 Review Request".
4. Wait 5 days.
5. Send the email template "MSS v1 - 15 Review Google".

Set sender name to "My Salon Suite Blaine" and sender email to
"scleveland@mysalonsuite.com" for all emails. Save as draft.
```

---

## After AI builds each workflow — quick checklist

- [ ] Open each Send Email step and confirm the correct template is selected
      (the AI matches by name, but double-check the template thumbnail).
- [ ] Workflow 1: confirm the trigger points at your real Book-a-Tour form.
- [ ] Workflow 3 & 4: the tag "lease-signed" must exist
      (Contacts › Tags › New Tag) before publishing.
- [ ] Map the form's time-preference question to the custom field
      "Preferred Tour Time" so {{contact.preferred_time}} populates.
- [ ] Update "MSS v2 - 01 Tour Requested" once the Calendly URL is provided.
- [ ] Send a test submission, confirm the first email arrives, THEN publish.
```
