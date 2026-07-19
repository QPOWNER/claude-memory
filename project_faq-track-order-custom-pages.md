---
name: faq-track-order-custom-pages
description: Both FAQ apps (FAQ Prime + HelpCenter) replaced 7/19/26 with custom-coded /pages/faqs-1 (31 Q&As) and /pages/track-order-1; user must uninstall both apps
metadata: 
  node_type: memory
  type: project
  originSessionId: 1582dcf3-24cf-455c-8921-a3ae2f6d1c58
---

On 7/19/26 BOTH FAQ apps were replaced with self-contained HTML/CSS/JS written directly into Shopify page bodies via Admin GraphQL — no theme edits, so the [[customizer-art-pipeline]] theme-clobbering risk doesn't apply:

- **FAQ Prime** (faqprime.com, "faqlite" embeds): powered old /pages/faqs-1 + /pages/track-order-1 with never-customized stock text (UPI/Paytm payments, 7-vs-30-day return conflict) + sitewide widget with WRONG WhatsApp number 716 848-0099.
- **HelpCenter | FAQ Chat Helpdesk** (eoscity, /apps/help-center proxy): hosted a real 56-article KB with good custom content — fully harvested and merged 7/19/26. Its theme embeds were already disabled/inert (product tabs are the theme's own pxu-tabs). Contained OUTDATED "We don't do Printing" answer referring customers to 5 Etsy competitor shops — deliberately NOT migrated.

Current state:
- `/pages/faqs-1` (gid://shopify/Page/101386584310): 31-question accordion, 6 categories, live search, FAQPage JSON-LD with all 31. Key facts: blanks ship same-day by 4 PM EST, custom ready 2–4 business days after mockup approval, free shipping >$45 via USPS/UPS/FedEx, no PO boxes, APO yes / Canada no, 30-day returns (customer pays return shipping, refund 3–5 days, promo purchases non-refundable), MOQ 6 custom / none blank, tax-exempt certs accepted, metallic koozies can't be sublimated/DTF'd, defect-sale collection for practice.
- `/pages/track-order-1` (gid://shopify/Page/101386617078): tracking instructions + account orders button.
- Header menu FAQ item → /pages/faqs-1 (PAGE type).
- To add/edit questions: pageUpdate the body (each Q = details block + matching JSON-LD entry).

**Outstanding for user:** uninstall BOTH apps in Shopify admin (FAQ Prime + HelpCenter). Conflicts RESOLVED 7/19/26 per user: custom turnaround = 3–5 business days (FAQ corrected); free shipping = $45 (announcement bar + header promo fixed 35→45 via CLI settings_data.json push, 4 spots); "We don't do Printing" KB answer confirmed for deletion (dies with HelpCenter uninstall). Still open: "Coolie Nation" wrong-brand disclaimer in FAQ page theme section (separate task session running).

**Remaining FAQ candidates needing user input:** custom-item return policy, artwork file requirements, copyrighted-design policy.
