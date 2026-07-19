---
name: custom-shipping-profile
description: "Customizer/personalized products ship via \"Custom Shipping USA\" delivery profile — flat rates with \"Ships in 3-5 Business Days\" naming, NO live carrier rates (they show misleading arrival dates)"
metadata: 
  node_type: memory
  type: project
  originSessionId: 18d081f1-ab2c-4e98-828a-cf1f1d52813b
---

Shopify delivery profile **"Custom Shipping USA"** (gid://shopify/DeliveryProfile/95998312694, location group 97195720950, zone "Small Packages" 388030595318) holds ALL personalized/customizer products (~130 variants incl. the 6 customizer products, older Personalized listings, Design Recreation + Expedited Printing add-ons — add-ons live here so mixed carts don't stack rates from two profiles). Set up 7/19/26 after merchant complained checkout promised "tomorrow" on custom orders.

Rates (final state 7/19/26 evening — merchant pared back to free-only; manual rates show NO arrival date at checkout):
- **Free Shipping 2-4 Business Days — Custom Made, Ships in 3-5 Business Days** — $0, orders ≥ $45 (def 602915012854)
- **Standard Shipping — Custom Made, Ships in 3-5 Business Days** — $6.95, orders ≤ $44.99 (kept so sub-$45 carts can check out; def 853008908534)
- Priority $9.95 + UPS 2nd Day (2 tiers) + Next Day (2 tiers) were added then DELETED same day per merchant "for now just free shipping" — instead, expedited air is handled by contact: **"✈️ Need it faster? … (716) 415-0354 / sales@quality-perfection.com"** line in product-customizer.liquid (class qp-rush-ship, under the #qp-eta block — survives via the shared section, check after clobbered pulls). Public contact = (716) 415-0354 text/call/WhatsApp + sales@ (same as FAQ).

**Local delivery ($10, 23 ZIPs, $35 min) is ON** — I disabled it 7/19/26 misreading "change from local shipping to pickup 0$", merchant corrected ("I just asked to add pickup, not delete everything") → re-enabled same day; toggling off/on preserves the zone config. Free Local Pickup is ALSO on (2-hr window, text-first instructions, location 58018070724): it's the "Pickup" TAB at top of checkout, never a line in the shipping list. Local delivery is location-level (no Admin API — admin UI only: Settings > Shipping > Local delivery); affects ALL products. **Lesson: "change X to Y" from this merchant may mean "add Y" — confirm before removing anything that exists.**

Expedited tiers are PRICE-based, not weight-based — customizer variants all have weight 0 (virtual quantity-tier products), so weight conditions never differentiate. ~$200 subtotal ≈ 90 units ≈ 5 lb. Expedited transit pairs with the Expedited Printing — Rush Add-On for actual fast turnaround (transit speed alone doesn't skip the 3-5 day production).

**Why:** live USPS/UPS carrier rates display carrier-computed arrival dates (e.g. "Tue, Jul 21") that ignore production time — impossible to offset via API — so they were DELETED from this profile 7/19/26. General + "usa" profiles (stock products) still have carrier rates + "Free Shipping 2-3 Business Days" — correct for in-stock items; do NOT rename those.

**How to apply:** new customizer products MUST be added to this profile (deliveryProfileUpdate variantsToAssociate with ALL variant ids) or they fall back to the General profile's 2-3-day promise. **GOTCHA (bit us 7/19/26): profiles are per-VARIANT — variants created AFTER a product joined the profile (e.g. quantity-tier variants added to Personalized Standard 12oz) land in the General profile silently.** The regular customizer's 7 tier variants showed "2-3 Business Days" until re-associated (profile count 129→136). After adding variants to ANY personalized product, re-run variantsToAssociate for all its variants (re-associating is a harmless no-op), then verify with a cart permalink for the SPECIFIC new variant. Admin's "fulfill by Monday" SLA on custom orders derives from rate names — cosmetic, safe to ignore. The shipping settings admin page is too heavy for the Chrome extension (screenshot/read_page timeouts) — use the delivery profile GraphQL API instead; verify rates by driving a real cart permalink (/cart/VARIANT:QTY?checkout) through Shop Pay checkout and get_page_text. Merchant's Shop Pay auto-redirects; NEVER click Pay now.

Related: [[customizer-art-pipeline]], [[approval-mockup-email]]
