---
name: faq-track-order-custom-pages
description: FAQ Prime app replaced 7/19/26 with custom-coded /pages/faqs-1 and /pages/track-order-1 page bodies; user must uninstall the app
metadata: 
  node_type: memory
  type: project
  originSessionId: 1582dcf3-24cf-455c-8921-a3ae2f6d1c58
---

On 7/19/26 the FAQ Prime app (faqprime.com, "faqlite" embed divs) was replaced with self-contained HTML/CSS/JS written directly into Shopify page bodies via Admin GraphQL — no theme edits, so the [[customizer-art-pipeline]] theme-clobbering risk doesn't apply:

- `/pages/faqs-1` (gid://shopify/Page/101386584310): 11-question accordion (native details/summary), live search filter, FAQPage JSON-LD schema (feeds [[aeo-content-pipeline]]). Answers grounded in real store policies: 30-day returns, free shipping over $45, no PO boxes, cards + Shop Pay/Apple Pay/Google Pay, custom MOQ 6 units, production 3–5 business days after mockup approval.
- `/pages/track-order-1` (gid://shopify/Page/101386617078): tracking instructions + button to customer account orders (https://shopify.com/51435667652/account/orders) + contact fallback.
- Header menu (gid://shopify/Menu/182452781252) "FAQ" item repointed from /apps/help-center (app proxy) to /pages/faqs-1 as PAGE type.

**Outstanding:** user must uninstall FAQ Prime in Shopify admin (this also removes the floating "Help"/WhatsApp widget sitewide — WhatsApp number in it was +1 716 848-0099). Scratchpad sources were saved as faq-page.html / track-order-page.html (session-temporary; canonical copy lives in the Shopify page bodies).
