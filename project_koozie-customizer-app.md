---
name: koozie-customizer-app
description: Shopify App Store app version of the QP customizer — Remix scaffold + theme app extension live in Documents\koozie-customizer-app\koozie-customizer
metadata: 
  node_type: memory
  type: project
  originSessionId: a8f582fb-195f-4492-acd9-ad4a66ed6794
---

User is turning the theme-embedded customizer (see [[customizer-art-pipeline]]) into a public Shopify App Store app. Started 2026-07-19.

**State (2026-07-19):** Phase 1 (proof of concept) built and `shopify app build` passes clean:
- App scaffold: `C:\Users\qpllc\Documents\koozie-customizer-app\koozie-customizer` (Remix JS template, Prisma/SQLite sessions, client_id 4b896b63f8ebf9c2cb984fc6e8a34cd7 already in shopify.app.toml — CLI created it non-interactively via cached sales@ auth).
- Theme app extension: `extensions/koozie-customizer/` — section ported to app block (`blocks/customizer.liquid`, section.settings→block.settings, target "section", presets removed), 105 assets (8 MB, pmax-* excluded), Fabric.js 5.3.1 vendored from cdnjs into assets (was external CDN).
- Key design: JS references 4,613 qpa-*.webp art tiles — far too big to bundle. Added block setting `asset_base_css_url` (default = QP live theme CDN `https://www.quality-perfection.com/cdn/shop/t/38/assets/qp-customizer.css?v=...`) that overrides config `assetBase`; JS unchanged. CORS verified OK (JS uses crossOrigin anonymous, Shopify CDN sends ACAO:*). Phase 2 = serve art from app backend.
- Remaining QP-hardcoded strings in JS (lines ~6303/6317/6827): share text, mailto body, custom@quality-perfection.com bulk-quote email — make merchant-configurable in Phase 2.

**PHASE 1 COMPLETE & VERIFIED (2026-07-19):** customizer renders fully on dev store `koozie-customizer-test.myshopify.com` (storefront password `cheeck`; Basic plan, test data; created via dev dashboard org "QualityPerfection" id 32557855, app id 399713435649). App deployed (`shopify app deploy --allow-updates`, no --force in CLI 4.x) and installed on the dev store.

Hard-won learnings:
- Theme app extension assets DON'T allow .webp (only jpg/png/svg/js/css/json/wasm) — all art/mockups load via `asset_base_css_url` setting from QP live CDN instead.
- App blocks allow max ONE `product`-type setting (stock_product removed; `product_list` is fine).
- Template JSON app-block type needs a server-side UUIDv7 (`shopify://apps/koozie-customizer/blocks/customizer/019f7ade-9e64-73c5-8428-873ccdcd6095`) that is NOT the toml/manifest uid — unobtainable locally; get it by using the theme-editor deep link `?template=index&addAppBlockId=<client_id>/customizer&target=newAppsSection` then Save and `shopify theme pull`. Pushing an invalid app-block type silently strips the block server-side.
- `shopify app dev` unusable non-interactively (storefront password prompt ignores env vars); deploy+install flow works instead.
- Theme editor in claude-in-chrome background tab stalls forever (pending XHRs) — user must foreground the tab and click Save.
- `shopify theme pull/push --store=koozie-customizer-test.myshopify.com --theme 147868090428` works with cached sales@ CLI auth.

**Order flow VERIFIED (7/19/26):** test product `the-complete-snowboard` wired to block; driven via page JS — cart line item carries Custom Text/Font/Koozie Color/Print Sides + _Design Data + _Preview Front + _Design File Front uploaded to the dev store's own CDN. Full pipeline works cross-store. Print-area fix deployed as v3 (live values 30/35/41/41 vs stale defaults 22/20/56/60 — pull live config from the page's #qp-customizer-config JSON when in doubt).

**Competitive scan done (7/19/26, agent-researched):** NO koozie/drinkware/promo-niche customizer exists on App Store. Incumbents: Zakeke $70-300+1.5-1.9% fee, Customily $49+per-item fee (20-min renders!), Teeinblue $49+fees, Zepto $10-50 (pricing bugs), Inkybay $20-250 (-13% YoY), Qstomizer $10-50. Recommendation: $19 Starter / $49 Pro, NO per-order fees (key differentiator for bulk), 21-day trial. Three things to nail: render speed/reliability, US-hours support, setup simplicity + bulletproof pricing math. "Built by a koozie print shop" = the marketing angle.

**Product presets shipped (v4, 7/19/26):** block setting `product_preset` (16 options: 5 koozie types with real live-page values — Regular 30/35/41/41 3×3, Slim 33/27/34/55 2.9×4, 16oz 33/30/33/50 3.2×4, magnetics = one-side; mug 11/15oz, tumbler 20oz, stadium cup, tshirt, hoodie, tote, hat, coaster, sticker, custom). Non-koozie presets emit `mockupPrefix: null` → JS (one-line change at colorPickerActive) hides koozie-color select; merchant uploads own product photo via existing mockup_image picker, else drawn placeholder. Non-koozie print-area numbers are industry-standard estimates — merchants fine-tune; QP should validate mug/shirt values when adding those products.

**White-label shipped (v5, 7/19/26):** zero quality-perfection strings left in extension JS — share/mailto text uses window.location.hostname, bulk-quote contact is new block setting `quote_email` (config key quoteEmail, blank = generic message). Remaining QP dependency: asset_base_css_url default → QP CDN (art library; moves to app backend with hosting).

**Billing + GDPR shipped (v6, 7/19/26):** shopify.server.js has billing config (STARTER_PLAN $19 / PRO_PLAN $49, Every30Days, trialDays 21; isTestBilling() = test charges unless env BILLING_LIVE=true). app/routes/app.billing.jsx = Polaris plan page (subscribe/switch via billing.request — approval auto-replaces sub = up/downgrade compliant; cancel w/ prorate). Remix gotcha: route component can't import shopify.server — plan names are UI literals, loader/action use dynamic import. webhooks.compliance.jsx handles customers/data_request, customers/redact, shop/redact (ack-only, no customer data stored); registered in toml via compliance_topics. App-store precheck (7/19): everything else passes; remaining blockers = hosting/TLS only, then feature-gating (10-product Starter limit not enforced yet) + listing assets (icon, screenshots, privacy policy URL).

**Phase 2 started:** app/routes/app._index.jsx rewritten as real Polaris dashboard (setup steps + add-block deep link using SHOPIFY_API_KEY env + status/roadmap cards); `npm run build` passes. NOT visible in admin until the app is hosted (app_url still example.com) — next session: pick hosting (Railway/Fly ~$5/mo), deploy backend, update app_url; then art upload, billing, de-QP-branding, color-stock via app data. Phase 3 = listing + `shopify-app-store-review` precheck.
