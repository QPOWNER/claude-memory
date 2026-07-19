---
name: custom-shipping-profile
description: "Customizer/personalized products ship via \"Custom Shipping USA\" delivery profile — flat rates with \"Ships in 3-5 Business Days\" naming, NO live carrier rates (they show misleading arrival dates)"
metadata: 
  node_type: memory
  type: project
  originSessionId: 18d081f1-ab2c-4e98-828a-cf1f1d52813b
---

Shopify delivery profile **"Custom Shipping USA"** (gid://shopify/DeliveryProfile/95998312694, location group 97195720950, zone "Small Packages" 388030595318) holds ALL personalized/customizer products (~130 variants incl. the 6 customizer products, older Personalized listings, Design Recreation + Expedited Printing add-ons — add-ons live here so mixed carts don't stack rates from two profiles). Set up 7/19/26 after merchant complained checkout promised "tomorrow" on custom orders.

Rates (all names carry the production window; manual rates show NO arrival date at checkout):
- **Free Shipping — Custom Made, Ships in 3-5 Business Days** — $0, orders ≥ $45
- **Standard Shipping — Custom Made, Ships in 3-5 Business Days** — $6.95, orders ≤ $44.99
- **Priority Shipping — Custom Made, Ships in 3-5 Business Days** — $9.95, unconditioned

**Why:** live USPS/UPS carrier rates display carrier-computed arrival dates (e.g. "Tue, Jul 21") that ignore production time — impossible to offset via API — so they were DELETED from this profile 7/19/26. General + "usa" profiles (stock products) still have carrier rates + "Free Shipping 2-3 Business Days" — correct for in-stock items; do NOT rename those.

**How to apply:** new customizer products MUST be added to this profile (deliveryProfileUpdate variantsToAssociate with ALL variant ids) or they fall back to the General profile's 2-3-day promise. Admin's "fulfill by Monday" SLA on custom orders derives from rate names — cosmetic, safe to ignore. The shipping settings admin page is too heavy for the Chrome extension (screenshot/read_page timeouts) — use the delivery profile GraphQL API instead; verify rates by driving a real cart permalink (/cart/VARIANT:QTY?checkout) through Shop Pay checkout and get_page_text. Merchant's Shop Pay auto-redirects; NEVER click Pay now.

Related: [[customizer-art-pipeline]], [[approval-mockup-email]]
