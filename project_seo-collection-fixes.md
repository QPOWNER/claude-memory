---
name: seo-collection-fixes
description: "Jul 21 2026 SEO push: slim + foam-wholesale collections rewritten for 'koozie' keywords, product JSON-LD gained return/shipping/author fields, Organization schema added to live theme"
metadata: 
  node_type: memory
  type: project
  originSessionId: 418896c8-b4b2-47b3-af57-39a08d756d44
---

GSC 3-month check (Jul 21 2026): 1.43K clicks / 132K impr / CTR 1.1% / avg pos 10.7. Biggest gap found: "slim can koozie" 6,038 impr but pos 10.2 because /collections/slim head tags said "can cooler" not "koozie". foam-wholesale same problem at pos 16.4 (7,313 impr).

Fixed same day (baseline to compare against in ~3-4 weeks):
- Collection `slim` (gid 237724631236): title "Slim Solid Koozies"→"Slim Can Koozies", SEO title "Slim Can Koozies – 12oz Skinny Can Coolers, Blank & Bulk", new meta desc + 3-paragraph keyword description linking to bulk-blanks guide and /pages/design-your-koozie.
- Collection `foam-wholesale` (gid 396805832950): title now "Foam Koozies in Bulk – Wholesale Foam Can Coolers", SEO title/desc + description (had NONE before). Links to foam-vs-neoprene article + bulk guide.
- Bulk-blanks guide article (gid://shopify/Article/598516269302) now links to /collections/foam-wholesale (2x) and /collections/slim.
- `snippets/structured-data.liquid` on live theme 159858032886: Product offers gained validFrom, hasMerchantReturnPolicy (30d, ReturnByMail, customer pays — matches real refund policy), shippingDetails (US, 0-3d handling, 2-5d transit); review gained author (Organization=shop); added Organization schema (closes 7/16 scanner gap) + WebSite SearchAction. Cleared 4 of 5 GSC Merchant-listing warnings; NOT fixed initially: "Invalid value in field sku" — traced 7/21 to spaces in SKUs; fixed all 6 via productVariantsBulkUpdate (24/50 SLIMBLACK + WHITESLIM "X - NEO - QP"→"X-NEO-QP", KELLY GREEN→KELLYGREEN) on products 7946309140726 + 8074926424310. If Sumtracker/supplier mapping ever misses these SKUs, this rename is why. Remaining cosmetic warning: missing shippingRate inside shippingDetails — deliberately NOT added (rates vary per product; Merchant Center feed is authoritative). "Validate fix" clicked 7/21 for hasMerchantReturnPolicy (Started); other 3 validations not started — GSC tabs kept crashing; they clear on natural re-crawl. GSC drilldown rows need REAL mouse clicks (JS .click() and synthetic events don't fire GSC handlers).

**Why:** these edits live in Shopify data (safe) EXCEPT structured-data.liquid which a full theme push from the other machine would clobber — merge_all2.js does NOT cover it.

**How to apply:**
- Theme CLI works from scratchpad with explicit flags: `shopify theme pull/push --store qualityperfection.myshopify.com --theme 159858032886 --only "snippets/structured-data.liquid" --allow-live` (bare `shopify theme list` without --store fails with scope error).
- GSC Merchant listings UI: left nav Shopping > Merchant listings (deep-link URL guesses 404).
- Related: [[aeo-content-pipeline]], [[qp-site-scanner]], [[customizer-art-pipeline]].
- Scheduled task `weekly-website-improvement-check` (Mondays 9am, created 7/21/26) runs the full GSC + scanner + schema-integrity check and writes reports to Documents\QP-Weekly-SEO\ — don't duplicate it with ad-hoc checks unless the user asks.
- CLOUD version (runs with PC off): private repo QPOWNER/qp-weekly-seo (local clone Documents\QP-Weekly-SEO-Cloud), GitHub Action Mondays 13:00 UTC — dependency-free check.js pulls GSC API (service account) + curls live site for schema-clobber canary, commits report + opens issue. As of 7/21/26 user still needs to: create Google Cloud service account (README steps A-C), add repo secret GSC_SERVICE_ACCOUNT; site checks work without it. Storefront curls MUST use curl not Node fetch (Shopify edge 429s).
