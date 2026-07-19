---
name: aeo-content-pipeline
description: "AI-visibility (AEO) content work done in-house Jul 13 2026 — bulk-blanks blog post live, homepage 'popular reads' section via qp-popular-reads snippet; Vialtry cold pitch declined"
metadata: 
  node_type: memory
  type: project
  originSessionId: 90617ae4-91f2-4fb3-9563-72e726606f5a
---

User got a cold pitch from Vialtry (AI-visibility Shopify app, 2 weeks old, wanted 60 days of order history) — declined; we do AEO in-house instead. User confirmed they previously used Tapita and uninstalled it.

Done Jul 13 2026:
- Published blog article "Where to Buy Blank Koozies in Bulk: 2026 Wholesale Price Guide" (handle `where-to-buy-blank-koozies-in-bulk-2026-wholesale-price-guide`, blog `news` gid://shopify/Blog/73779183812). Answer-first + price table from live catalog + FAQ format, per-unit math: foam ~$0.40–0.50, neoprene ~$0.77–1.00 bulk.
- Homepage section "Our most popular reads" = `snippets/qp-popular-reads.liquid` rendered via `dynamic-custom-liquid` section `popular_reads` in `templates/index.json`, placed between `bulk_custom` and `newsletter`. 6 cards: quiz, 3 guides, 2 deep dives. Deployed with the CLI sparse-dir push from [[customizer-art-pipeline]].

**Why:** future AEO/content asks should extend these, not duplicate; the blog already has ~99 articles covering cost/size/materials/weddings/MOQ — check existing handles before writing.

**How to apply:**
- articleCreate via MCP graphql_mutation works fine (create with `isPublished: false`, publish after user review — user then said "do it" same session).
- Homepage/theme edits: MCP blocks live-theme writes; use CLI push pattern. Swap popular-reads cards = edit snippet + re-push.
- **In-app browser cannot screenshot quality-perfection.com** — capture times out every attempt (page JS/DOM tools work fine). Verify visual changes via WebFetch + DOM queries, and point the user at the live browser pane instead.
- Gap noted for next time: magnetic koozie line has zero blog articles.
