---
name: reviews-email-flows
description: Review collection (Vitals) + Shopify Messaging email automation state — what's fixed, what's pending; NO discounts per user
metadata:
  type: project
---

**User policy: NO discounts** — prices are already lowest (stated 8/2/26). Priority is MORE REVIEWS.

Reviews (Vitals app, $29.99/mo — Product Reviews module Active, widget live on product pages):
- Base: 154 published reviews, 4.95★ avg. Last 30d baseline: 74 request emails sent, **0 collected** — root cause was timing: requests fired **3 days after fulfillment**, i.e. before/at delivery ("did you open the box?" subject arrived before the box).
- FIXED 8/2/26: timing changed to **14 days after Order fulfilled**, saved. Reminder stays 7d after (≈day 21). Watch collected count in ~3 weeks in Vitals → Product Reviews dashboard.
- Next review levers (not done): Amazon request-a-review sweeps (3 ASINs under 4.6★, see [[amazon-review-audit]]); package-insert card with review QR (in-house DTF printing makes this ~free); add review ask to the "Thank you" automation.

Shopify Messaging email automations (Seguno is UNINSTALLED — this replaced it; sidebar Apps > Messaging > Automations):
- 30d: 35 sent, 5.7% click, 0 orders. Active: thank-you, welcome series, welcome subs, abandoned browse/cart/checkout. Inactive: Customer winback, Notify about new products, Recover abandoned cart (old dup — do NOT enable alongside Abandoned cart), birthday.
- Customer winback: subject added 8/2/26 ("We miss you — a special offer on your next koozie order") but template still DRAFT — requires selecting a discount + product to activate. User declined discounts → to activate, DELETE the Special Offer block (and fix subject wording) instead. Red ⚠ icons on 4 active automations are likely the same missing-discount template issue.
- Embedded-app UIs (Messaging, Vitals) are iframes: invisible to read_page/find; native selects work via click + arrow keys; row-menu clicks unreliable — use Edit automation → editor page. CC auto-mode classifier BLOCKS: create-discount MCP, typing marketing copy into fields (intermittent) — hand those to user.

Pinterest channel: installed, catalog Connected, 1,782 products approved. Ads paused: "update billing details" (user-only). Organic boards/pins = untapped; wedding/monogram assets exist.
Money leak: Sellerboard $9/mo still billing while [[qp-profit-dashboard]] waits on user's SP-API registration.

**Why:** these are the owner's chosen traffic/review levers; knowing exact state avoids re-auditing.
**How to apply:** never add discount-based flows; check Vitals collected-count ~8/23/26 to confirm the timing fix worked.
