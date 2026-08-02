---
name: bing-webmaster-tools
description: Bing Webmaster Tools state for quality-perfection.com — verified & fully plumbed; Site Scan + 316 identical-meta-description fix are the open items
metadata:
  type: project
---

Bing Webmaster Tools (bing.com/webmasters, sign-in lives in the user's real Chrome — the in-app browser pane has no session; use Claude-in-Chrome tools) already has quality-perfection.com verified and collecting data. Audited 2026-08-02:

- Sitemaps: both `https://www.` and `http://` sitemap.xml indexes discovered, crawling Success, 818 URLs total.
- IndexNow: live automatically via Shopify (92 product URLs submitted through 7/24/26) — no setup needed.
- Search perf (90d): 109 clicks / 9.8K impressions.
- AI Performance (Copilot citations, 90d): 630 citations, ~2 pages/day. Only 2 grounding queries: "quality perfection" (navigational, 47% citation share) and "vinyl material" (1.5%). **No koozie informational queries cited yet** — gap for [[aeo-content-pipeline]].
- 316 "identical meta descriptions" flag: FIXED 8/2/26 — wrote unique SEO descriptions via aliased productUpdate/collectionUpdate GraphQL batches (Shopify MCP): 55 of 81 active products (null seo or one of 4 recycled boilerplates: "FREE SHIPPING…Blank & Pattern", "Our Can Cooler Sleeves are Wholesale…", "Typically ships out…#kooziebulk", "Fabric Details…permit") + 45 of 51 collections (nearly all had null seo). Verified live via curl. Bing's flag clears on its next crawl (weeks). Blog articles have no seo field in Admin API (use metafield global.description_tag) — left alone, bodies are unique.
- Site Scan "QP full scan Aug 2026" started 8/2/26 BEFORE the fixes (600 pages of www, quota 1000/mo, 400 left) — results email to qpllc1@gmail.com; treat as pre-fix baseline, re-scan next month to confirm.

**Why:** Bing index feeds Copilot/ChatGPT answers, so BWT is part of the AEO work, not just SEO.
**How to apply:** don't re-verify or re-submit sitemaps/IndexNow, and don't re-fix product/collection metas — if the flag persists after a few weeks, the leftovers are likely paginated/filtered collection URLs, not Shopify resources; related: [[seo-collection-fixes]].
