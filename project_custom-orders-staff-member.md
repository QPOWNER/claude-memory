---
name: custom-orders-staff-member
description: Third-party staff member added 7/21/26 with view-only Orders access to work custom/customizer orders
metadata: 
  node_type: memory
  type: project
  originSessionId: 3ed2206e-cdfa-4400-962c-bcd5d664aa7c
---

7/21/26: User invited a third-party staff member to the Shopify store to manage custom orders. Permissions: only "View" + "Manage order information" under Orders (2/20) — no refunds, fulfillment, payments, settings, or pixels.

Verified on order #8789 that this is sufficient: customizer artwork appears as line item properties with public CDN links — `Customer Artwork Front/Back` (raw uploads), `_Design File Front/Back` (print-ready), `_Preview Front/Back` (mockups). View permission alone lets him download them.

Finding his queue: customizer orders have NO tags — he filters by product title contains "Personalized" or fulfillment status **On hold** (customizer orders sit ON_HOLD; retail orders don't). Related: [[customizer-art-pipeline]], [[approval-mockup-email]].
