---
name: approval-mockup-email
description: Standard workflow — every customizer order gets an approval-mockup email (Approve button) AFTER the print file is made print-ready
metadata: 
  node_type: memory
  type: project
  originSessionId: 18d081f1-ab2c-4e98-828a-cf1f1d52813b
---

For **every customizer order** (products tagged `customizer` / "Personalized …" line items with `_Design File`/`_Preview` properties): after checking/fixing the artwork so it's **good to print**, build an approval email and create a Gmail draft for the user to send. Established 7/19/26 (first one: order #8778).

**How to apply:**
1. Pull the order: line item `customAttributes` hold `_Preview Front/Back` (mockup PNG), `_Design File Front/Back` (print file), `Customer Artwork`, `Koozie Color`, `Print Sides`. Underscore-prefixed props are hidden in Shopify admin — that's normal.
2. First make the design print-ready (check resolution, transparency, placement), then send the approval email — approval always references the corrected mockup.
3. Fill the HTML template at `C:\Users\qpllc\Documents\QP-Approval-Email\approval-email-template.html` (placeholders: CUSTOMER_NAME, ORDER_NUMBER, ORDER_NUMBER_URLENC e.g. `%238778`, QTY, PRODUCT_TITLE, KOOZIE_COLOR, PRINT_SIDES, MOCKUP_URL).
4. Create a Gmail **draft** (never auto-send) to the customer's email. Subject: `Your Mockup Is Ready for Approval — Order #XXXX | QualityPerfection`. Green Approve button = mailto:sales@quality-perfection.com with pre-filled "APPROVED — Order #XXXX" reply; secondary "Request changes" mailto link.
5. Production note in email: starts only after approval, ships 3–5 business days after.

Checkout was changed 7/19/26 to contact method = **Email** (+ shipping phone Required), so all new orders have an email address. Older orders may be phone-only (like #8778) — draft to contact@quality-perfection.com and tell the user to get the customer's email.

Related: [[customizer-art-pipeline]], [[koozie-customizer-app]]
