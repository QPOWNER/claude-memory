---
name: amazon-review-audit
description: How to pull per-ASIN star ratings/review counts for the Amazon store; seller ID A1S6CDTXUH1ROG
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4f32a93d-553c-4958-83d3-3717fb3b5e88
  modified: 2026-07-24T15:48:51.815Z
---

Amazon seller ID (QualityPerfection): **A1S6CDTXUH1ROG**.

To audit ratings per ASIN: browse `https://www.amazon.com/s?me=A1S6CDTXUH1ROG&s=review-rank` in the user's Chrome (logged in, ~31 parent listings, 2 pages) and extract `data-asin` + `[aria-label*="out of 5 stars"]` + `[data-cy="reviews-block"]` text via javascript_tool. Variations collapse to parents, so this covers the full catalog (1,135 SKUs → ~31 rating pools). Seller Central merchant-token page is blocked by the permission classifier — get the seller ID from any product page's `seller=` link instead.

7/24/26 baseline: three ASINs under 4.6 — B0D5C2W49N (3.9★, 5), B0DJ68LQ83 (4.1★, 2), B0C1XX9TY8 (1.0★, 1). Related: [[qp-profit-dashboard]] (SP-API pending; once live, could automate).

**Child-ASIN drill-down (7/24/26)**: Amazon only publishes family-aggregate stars; per-child data must be computed from written reviews via `/product-reviews/<childASIN>?formatType=current_format` (header "N matching customer reviews" + page-1 stars; add `&filterByStar=` for exact histograms when N>10). Review pagination past page 1 is dead (even signed in) — filters are the only segmentation. ~350 fetches triggered a soft block ("Sorry! Something went wrong") — pace slower next time. 284 children scanned; full results in `Documents\Amazon-Reviews-By-Child-ASIN.csv`. Worst children by written reviews: B08GZQSL9T Tie Dye Mix 6U (4.09★/33), B01MRD00XU Mix Colors 12U foam (4.47★/224), B0C6FZ9DSM Camo Forest 1U magnetic (4.35★/23), B0GL3KYDYK Old Duck Camo 25U (1★/1). 64 child review pages 404 (suppressed variants); the 6 standalone cards incl. B0D5C2W49N/B0C1XX9TY8 have dead dp pages but still show in search.
