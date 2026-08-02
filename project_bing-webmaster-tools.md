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
- Open issue: 316 pages flagged "identical meta descriptions" (moderate). Homepage + main customizer products verified unique via curl — the dupes are the long tail (old products/filtered collections/blog). 
- Site Scan "QP full scan Aug 2026" started 8/2/26 (600 pages of www, quota 1000/mo) — results email goes to qpllc1@gmail.com; check scan report for the dupe-meta URL list, then fix in Shopify.

**Why:** Bing index feeds Copilot/ChatGPT answers, so BWT is part of the AEO work, not just SEO.
**How to apply:** don't re-verify or re-submit sitemaps/IndexNow — only work the scan results and meta-description dupes; related: [[seo-collection-fixes]].
