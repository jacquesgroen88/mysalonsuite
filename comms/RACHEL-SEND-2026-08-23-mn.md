# Rachel send — 23 Aug 2026 (the `mn` version)

*Reply on her "Re: DNS Updates Required" thread. Attach `My Salon Suite - Email and Booking Domain Setup.pdf`.*
*Supersedes `RACHEL-DNS-SEND-2026-08-20.md`, which says `mail` and must not be sent.*
*Stacey is already connected, so no calendar ask.*

---

**Subject:** Re: DNS Updates Required

Hi Rachel,

Agreed, and I've changed it. You're right that mail. on the main domain reads like Minnesota claiming something brand wide.

It's now mn.mysalonsuite.com, so emails come from stacey@mn.mysalonsuite.com and show as My Salon Suite Blaine. Clearly Minnesota, nothing corporate depends on it, and if another region wants the same setup later they can copy it.

Please ignore the sheet I sent Thursday and use the attached one instead. Renaming the subdomain regenerates the security key, so those old records are dead. They wouldn't throw an error, they'd just quietly not work, which is worse.

And yes, copy me in when you send it. Easier if I answer their technical questions directly than have you relay them.

Thanks,
Jacques

---

## Notes (do not send)

- The "ignore Thursday's sheet" line is the one that matters. If IT ends up with both versions they will add the wrong records and nothing will visibly fail.
- Do not mention that the sending domain never existed before last week. Ours to know, fixed, adds nothing for her.
- Not raised here: the two A2P website fixes on www.mysalonsuite.com/blaine/. Left out on purpose to keep this to one decision. Raise once the DNS is moving.
- She works Japan hours. Best window is roughly 06:00 to 10:00 SAST.
