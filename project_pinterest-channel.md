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

**Merchant Guidelines strikes — found 8/4/26** at `https://www.pinterest.com/reports-and-violations/` (also renders blank for ~10s; use `read_page`, not screenshots):
- **25 Pins Deactivated**, all cited under **Merchant Guidelines**, all typed "Created Pin" (manually created, NOT catalog-generated product pins). Dates: 23 on Aug 3, 1 on Aug 2, 1 on Jul 31, 2026. Single page — that's the full list.
- **24 of 25 are marked "Appeal reviewed" and are still Deactivated** — appeals already filed and already lost. Their `...` menu offers only "Review Community Guidelines" / "Visit help center", no appeal path left. Only the Jul 31 row still shows "Appeal decision" as an available action.
- **Every one uses the same image**: the multi-product color/pattern grid chart (thumbnail header reads "Regular Slim Pattern") — a swatch sheet showing dozens of koozies at once.
- **Stated reason (confirmed from the PDFs, 8/5/26): "violates our Merchant Guidelines on prohibited products, because it contains adult products and content."** Not a format/collage problem — Pinterest classified koozie swatch-chart Pins as adult products. Decisions were made by **human review**, found through **Pinterest's own investigation** (not user reports).
- Real timeline: deactivations landed **Jul 31 – Aug 1**; appeals were filed and **denied Aug 3** ("No change to decision", same reason). The "Aug 3" dates in the violations table are appeal-denial dates, not takedown dates.
- All 25 were on the board **"Products"**. Sample Pin IDs: `4601201189505373056` (Jul 31, generic reason, STILL APPEALABLE), `4592545798896609664` (Aug 1, adult reason), `4605634424227746688` (Aug 1 deactivated → Aug 3 appeal denied).
- "View full details (PDF)" silently downloads `StatementOfReasonsReport_<enforcementID>.pdf` to `C:\Users\qpllc\Downloads` — no new tab, no visible UI change. Check Downloads after clicking.
- **8/5/26: appeal submitted on Pin `4601201189505373056`** (the only one still eligible) arguing misclassification — koozies are general-merchandise drinkware, not adult products; cited Verified Merchant + Approved status + Shopify catalog. Row now reads **"Appeal in progress"**. Pinterest responds within 72 hours → **check back ~8/8/26**. If this one is reinstated, it's proof of misclassification worth taking to a Pinterest Partner Manager (schedule-a-call link is on the Business Hub) for the other 24, whose appeals are exhausted.
- Appeal dialog: row `...` menu → "Appeal decision" → free-text box, **1200 char limit**, Submit. Confirmation reads "Appeal submitted."
- Every notice carries: "If we discover more content that violates our terms... we may take additional action on your account, such as deactivating it." **Account-deactivation risk is live — audit the Products board before pinning anything new, and do not re-upload the swatch-grid image.**
- Account itself is NOT restricted — merchant status still Approved, catalog ingesting normally. Pin-level only.
- Timing caveat: the strikes land 7/31–8/3, but the organic decline spans the full 30 days — the deactivations are the tail end, not the whole cause.

Related: [[project_aeo-content-pipeline]] (the blog articles these pins point at), [[project_bing-webmaster-tools]].
