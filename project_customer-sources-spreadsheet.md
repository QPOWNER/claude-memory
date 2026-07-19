---
name: customer-sources-spreadsheet
description: Standing workflow — every customer/order the user asks about gets its acquisition source appended to Customer-Sources.xlsx
metadata: 
  node_type: memory
  type: project
  originSessionId: 2e6a83c5-c72b-4ee1-a497-8a522eaad501
---

The user tracks where customers come from in `C:\Users\qpllc\Documents\Customer-Sources.xlsx` (sheet "Customer Sources", created 2026-07-07 with the 13 customers investigated that day, orders #8705–#8726). NOTE: OneDrive was uninstalled and Documents/Desktop/Pictures repointed to plain local paths on 2026-07-07 at the user's request — the user does NOT want OneDrive. Leftover copies remain in `C:\Users\qpllc\OneDrive\` and in the cloud at onedrive.com.

**Why:** The user wants a running log of customer acquisition sources. Recent finding: the free Google Shopping feed (UTM `source=google, medium=product_sync, campaign=sag_organic` from the Google & YouTube channel app) drives ~80% of new customers.

**How to apply:** Whenever the user sends a customer name or order number, (1) look up the order in Shopify via GraphQL — pull `customerJourneySummary` (firstVisit source/referrer/landingPage/utmParameters), customer, total, ship-to; (2) append one row to the spreadsheet. Columns A–H: Date (order, yyyy-mm-dd) | Order # | Customer | Email | Source | Detail / Landing Page | Total ($) | Ship To.

Technical notes: no Python on this PC — append via Excel COM in PowerShell (`New-Object -ComObject Excel.Application`; find last used row, write cells, save). Assign Value2 with explicit `[string]`/`[double]` casts on separate lines or PS 5.1 COM binding throws InvalidCastException. Body font Arial 10; column G format `$#,##0.00`. Related: [[koozie-pricing-calculator-page]], [[draft-order-from-quote-request]].
