---
name: qp-site-scanner
description: "Local Node tool at Documents\\QP-Site-Scanner\\scan.js — AI-visibility/SEO/GEO/perf/security/indexing audit of any URL, HTML report output"
metadata: 
  node_type: memory
  type: project
  originSessionId: 0e64d662-3c0d-4977-9504-ffb58d08cf85
---

Built 7/16/26 after user saw a Hebrew SaaS post ("OSINT AI" site scanner) and asked "can you build this?" — replaces Vialtry-type vendors (declined 7/13/26, see [[aeo-content-pipeline]]).

**Tool:** `node C:\Users\qpllc\Documents\QP-Site-Scanner\scan.js <url> [--json]` — zero npm deps (Node 24 installed). Scores 6 categories (AI visibility, SEO, Performance, GEO, Security, Indexing) + engine-access tables (8 AI + 6 search crawlers, robots.txt verdict + live UA probe with browser-UA control), writes styled HTML report next to the script.

**Key facts learned:**
- quality-perfection.com scored **90/100** on 7/16/26 (AI 100, SEO 94, Perf 65, GEO 86, Sec 93, Index 100). All AI crawlers allowed; llms.txt exists (Shopify auto-serves it); FAQPage JSON-LD present but **no Organization schema on homepage** (top GEO gap); 719 KB homepage HTML + 101 scripts = main perf drag; title tag 70 chars (slightly long).
- Shopify/Cloudflare edge 429s Node's fetch (bot scoring) but passes curl — scanner auto-escalates fetch → retry → curl fallback; probe results marked "inconclusive" when the browser-UA control probe is also blocked.
- In-app browser screenshots time out on this machine (any page, not just storefront) — verify rendering via get_page_text / javascript_tool metrics instead.

**How to apply:** rerun before/after AEO changes to track scores; works on any URL (competitors too). Possible v2 the user hasn't asked for yet: rank tracking/competitors (needs paid SERP API), weekly scheduled run, multi-page crawl.
