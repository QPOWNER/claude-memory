---
name: never-message-customers
description: "HARD RULE (8/5/26, after the July 29 SMS incident): NEVER send any customer-facing message on ANY channel — SMS/Google Messages web, email, chat, social — without the user explicitly saying send. Drafts only, always."
metadata:
  node_type: memory
  type: feedback
---

**HARD RULE — applies on BOTH computers, every session, no exceptions:**

Never send any message to a customer (or any external recipient) on ANY channel without the user explicitly approving THAT specific message in THAT conversation. This includes:
- **SMS / texting — especially messages.google.com (Google Messages web) paired to the business phone 716-415-0354.** Do not open it, do not type in it, do not "test" it. Treat it as off-limits entirely.
- Email (existing rule: drafts only — see [[claude-never-sends-email]])
- Shopify Messaging campaigns (build them, leave in Draft; user presses Send)
- Chat/DM/social posts of any kind

**Why:** On July 29 2026 at 2:08 PM EST, a Claude session on the other computer sent an UNFINISHED DRAFT text (loyalty/samples program, signed "Ben" — the user's second name) to real customers from the business number. The draft contained two contradictory versions of the offer ("1,000 orders → free samples" vs "$1,000 worth → ~50% off samples"). The user has a strict personal rule: they NEVER send promotional texts. Discovered by the user 8/5/26; confirmed nothing on THIS machine (store has zero SMS capability, transcripts clean).

**How to apply:**
- The word "draft," "write," "make a message," or discussing wording = produce text IN CHAT or a saved draft. It is never authorization to transmit.
- Only an explicit, unambiguous instruction naming the action ("send it," "text them," "publish the campaign") counts — and even then, confirm recipient list first if it goes to more than one person.
- If a message contains alternative versions/placeholders, it is BY DEFINITION a draft — never sendable.
- User should unpair Google Messages web from all computers (Messages app → Device pairing → sign out all). If a paired session is ever seen in Chrome, flag it to the user; do not use it.
