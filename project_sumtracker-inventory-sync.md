---
name: sumtracker-inventory-sync
description: "Sumtracker multichannel inventory setup — state, decisions, and remaining steps"
metadata: 
  node_type: memory
  type: project
  originSessionId: 350d358d-e180-4121-a5fd-9fef5b9b7636
---

User chose Sumtracker (inventory.sumtracker.com, workspace "Quality") over Veeqo because they refuse to share company data with Amazon. Trial started ~7/19/26 (14 days).

**State as of 7/19/26:**
- Shopify (QualityPerfection): connected, Sync ON
- Amazon US (Seller A1S6CDTXUH1ROG): connected, wizard COMPLETE but Sync OFF deliberately — user must do a physical warehouse count first because Shopify quantities do NOT match the physical warehouse
- Wizard choices: FBA enabled (dedicated FBA warehouse), FBM warehouse = 2700 Commerce Parkway, "Copy my Amazon inventory" into 2700 COMMERC (runs when sync turns on), Return Sync disabled
- Etsy: connected 7/19/26, inventory sync disabled (orders sync in only) — enable after stocktake
- Stocktake "Full Count - 2700 Commerce Warehouse - July 2026" created 7/19/26 (id 2214, Draft) with ALL 2,505 products added; user clicks Start Counting, enters physical counts, Complete adjusts stock automatically

**SKU fixes applied in Shopify 7/19/26** (via productVariantsBulkUpdate): 300-box Slim/Sage → 300SAGE-SLIM-QP; Buffalo Plaid 50ct → 50BUFFALO-SLIM-QP (intentionally shared with Pattern 50/100 listing); Pattern 50/Desert Camo → 50DESERT-SLIM-QP. Gulf Of America / You Missed duplicate SKUs are INTENTIONAL dual listings (Trump Collection ↔ Pattern Regular) — do not "fix".

**Outstanding:**
1. 95 active Shopify variants still have NO SKU (foam blanks, 6-unit blanks, defect listings, all Personalized customizer products) — offered to generate following `{qty}{DESIGN}-{SIZE}-QP` convention
2. Physical stocktake → enter counts in Sumtracker (bulk sheet) → then Turn on Sync for Amazon
3. Connect Etsy
4. 300-box listing SKUs are scrambled vs color names (unique, sync-safe, just confusing) — optional cleanup

**Rule the user learned:** once Sumtracker is inventory master, never edit stock in Shopify admin — it gets overwritten; all adjustments go in Sumtracker.
