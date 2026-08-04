---
name: project_pinterest-channel
description: QualityPerfection Pinterest business account — merchant approved, Shopify catalog synced, organic down ~50%, zero ad delivery; baseline 8/4/26
metadata:
  type: project
---

Pinterest business account for quality-perfection.com. Handle `@qualityperfection`, verified, advertiser ID `549756929128`.

**Where to look** (Chrome has the session; the in-app browser does not):
- Business Hub: `https://www.pinterest.com/business/hub/`
- Organic analytics: `https://analytics.pinterest.com/` (redirects to `/overview/`). NOTE: `pinterest.com/business/hub/analytics/` 404s — don't use it.
- Ads reporting: `https://ads.pinterest.com/advertiser/549756929128/reporting/campaigns/`
- All three render lazily and screenshot blank for ~5s. Use `get_page_text` / `read_page`, not screenshots. Trend arrows (up vs down) only appear in `read_page` as `img "Trending down"` — `get_page_text` shows the % with no direction.

**Baseline 8/4/2026** (last 30 days, 7/5–8/4, vs prior 30):
- Impressions 6.53k (down 51%) · Engagements 301 (down 55%) · Outbound clicks 41 (down 45%) · Saves 5 (down 66%) · Total audience 5.26k (down 49%) · Engaged audience 257 (down 52%). Every metric down.
- Conversion insights: revenue $0.00, checkouts 0, page visits 103.
- Merchant status Approved, Event Quality Score "Good setup", Shopify data source Completed, 1,782 products, last ingestion 8/3/2026.
- Ads: 14 campaigns lifetime, 3 flagged Active, but the "Has Delivery" filter returns **0 campaigns** — nothing has served or spent in 30 days.

**The shape of the problem:** 5.36k of the 6.53k impressions come from one board, "What is ?" (10 pins) — the informational blog pins (What is Embroidery / DTG / DTF / Screen Printing / Sublimation). "What is Embroidery?" alone is 3.66k impressions, 228 engagements. Product pins are at ~0 impressions each. So the account gets traffic on top-of-funnel content that doesn't sell koozies, and the 1,782-product catalog gets nothing.

Pinterest is pushing a pre-built Performance+ catalog sales campaign at $20/day (est. 0–14 checkouts/week). Not launched — user has not decided. Compare against PMax at $60/day (see [[project_pmax-ad-kit]]) before adding spend.

Related: [[project_aeo-content-pipeline]] (the blog articles these pins point at), [[project_bing-webmaster-tools]].
