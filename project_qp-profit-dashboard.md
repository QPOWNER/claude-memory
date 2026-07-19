---
name: qp-profit-dashboard
description: "Self-hosted Sellerboard replacement (Amazon profit dashboard) in Documents\\QP-Profit-Dashboard — built 7/19/26, waiting on user's SP-API developer registration"
metadata: 
  node_type: memory
  type: project
  originSessionId: c4c65261-66c4-49e0-bc3d-71e3959f4df8
---

User is replacing Sellerboard ($30/mo, account yanivbiz1@gmail.com — Amazon: ~$155K sales, $45K net profit YTD 2026, FBA+FBM) with a self-hosted dashboard I built 7/19/26 in `C:\Users\qpllc\Documents\QP-Profit-Dashboard` (zero-dependency Node 24: `server.js` → http://localhost:4180, `sync.js` pulls SP-API orders/finances/traffic into `data\*.json` monthly files, `import-cogs.js`, `make-demo-data.js` for preview; launch.json entry `qp-profit-dashboard`). User only uses the profit dashboard, no other Sellerboard features → safe to cancel once live.

**Status / next steps:**
1. User must do one-time SP-API self-authorization in Seller Central (Apps & Services → Develop Apps) per `SETUP.md`, then fill `config.json` (LWA client id/secret + refresh token). Amazon approval can take days.
2. ✅ COGS DONE 7/19/26: all 1,212 SKU costs scraped from Sellerboard's internal getProducts API (via Angular scope + DOM-injection trick to beat the 1KB JS-tool output cap) → `data\cogs.json` + raw backup `data\cogs-sellerboard-backup-2026-07-19.json`. 185 SKUs are $0 in Sellerboard itself (mostly custom/multipack). make-demo-data.js is guarded against clobbering real cogs.json.
3. First `node sync.js` backfills from Jan 1 of prior year (30–90 min); delete demo `orders-*/finance-*/traffic-*/meta.json` first but KEEP cogs.json.
4. `sync.js` is untested against the real API (no creds yet) — expect to debug field names on first real sync, especially Finances event casing and GET_SALES_AND_TRAFFIC_REPORT options.

**Known gaps:** ad spend is ledger total only (per-product ACOS would need Amazon Ads API approval); no payout estimate/alerts/repricer. Validate a finished month against Sellerboard before cancelling. 185 zero-cost SKUs (mostly CUSTOMN-* custom prints) could be filled in later for better accuracy than Sellerboard ever had. Everything is local-only on this PC (user preference — no cloud); if the ASUS RMA takes the machine, copy the whole folder + Node to another PC. Offered but not yet built: desktop shortcut that starts server + opens browser.
