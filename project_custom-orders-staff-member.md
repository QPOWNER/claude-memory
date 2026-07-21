---
name: custom-orders-staff-member
description: Third-party staff member added 7/21/26 with view-only Orders access to work custom/customizer orders
metadata: 
  node_type: memory
  type: project
  originSessionId: 3ed2206e-cdfa-4400-962c-bcd5d664aa7c
---

7/21/26: User added Md Robiul Islam Rony, a third-party contractor, to manage custom orders. Shopify Basic has no staff seats, so he's a **collaborator** (free, via Dev Dashboard at dev.shopify.com — old partners.shopify.com signup is invite-only now). Role: only "View" + "Manage order information" under Orders (2/20) — no refunds, fulfillment, payments, settings, or pixels.

Company email: **rony-custom@quality-perfection.com** (Workspace user). contact@ has **mail delegation** into his mailbox (set 7/21/26; "leave unread when opened by others"; survives his password changes). Domain-wide "Mail delegation" toggle was enabled in Admin console → Gmail → User settings for this. Note: custom@quality-perfection.com = "Designer at QP", a DIFFERENT active person's account.

Webp quirk: Shopify CDN serves artwork links as webp when the browser advertises webp support even though stored files are PNG/JPEG — fix: right-click → Save link as, or convert (Paint/IrfanView). Print-ready art = `_Design File` properties; raw uploads = `Customer Artwork`.

Verified on order #8789 that this is sufficient: customizer artwork appears as line item properties with public CDN links — `Customer Artwork Front/Back` (raw uploads), `_Design File Front/Back` (print-ready), `_Preview Front/Back` (mockups). View permission alone lets him download them.

Finding his queue: customizer orders have NO tags — he filters by product title contains "Personalized" or fulfillment status **On hold** (customizer orders sit ON_HOLD; retail orders don't). Related: [[customizer-art-pipeline]], [[approval-mockup-email]].
