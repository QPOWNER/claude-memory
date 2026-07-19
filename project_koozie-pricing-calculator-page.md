---
name: koozie-pricing-calculator-page
description: "Shopify page \"Custom Koozie© Pricing Calculator\" embeds Tally form D4y7yN for quote requests with file uploads"
metadata: 
  node_type: memory
  type: project
  originSessionId: 10c297ad-4eff-4b38-a4b2-b50a9f04488a
---

Shopify page gid://shopify/Page/131691446518 (handle: koozie-pricing-calculator) on quality-perfection.com is an interactive pricing calculator. On 2026-07-05 the old /contact form (which silently dropped file uploads) was replaced with an embedded Tally form https://tally.so/forms/D4y7yN (public: tally.so/r/D4y7yN).

- The embed loads on "Send Quote Request →" click and passes `quote=<full calculator quote>` and `quantity=` as URL params.
- The Tally form has a hidden field named `quote`, so submissions automatically include the calculator quote. The "Estimated quantity" field was deleted 2026-07-05 (quantity lives inside the quote text).
- Form fields: name (req), email (req), company, phone, 2 file uploads (JPEG/SVG/PDF/PNG, 10 MB), "Anything else we should know?" textarea.
- Submissions/files are viewed in the Tally dashboard; related workflow: [[draft-order-from-quote-request]].
- **2026-07-05 price raise (+20%)** on neoprene custom printing (magnetic unchanged). Current tiers — Regular 12oz: $2.46 (6–11) / $2.34 (12–24) / $2.22 (25–49) / $2.10 (50–99) / $1.98 (100+); Slim: $2.58 / $2.46 / $2.34 / $2.22 / $2.10; 16oz: $3.12 (6–11) / $2.82 (12–24). Draft orders for quote requests must use these prices. Prices live in THREE places in the page body — static HTML table, JS `tiers` + `nextTier` arrays, and the default result panel ($2.22 / $55.50 for 25) — all must be kept in sync when editing.
- Page also has a "Real Price Comparison" section that NAMES competitors (user approved 2026-07-05), date-stamped July 5, 2026 with "prices may have changed" disclaimer: 25 units at QP $55.50 all-in (full color 2 sides, free ship) vs CustomLanyard.net $103.84 ($71.10 + $23.75 ship + $8.99 "Stealth Order Protection") vs 24HourWristbands.com $100.25 vs Imprint.com $100.25 (both $76.50 incl $10 setup + $23.75 ship) — all competitors 1 ink color 2 sides (user confirmed 2-sided). Note: all three competitor sites are the same Houston-based operator (identical carts/pricing). Mystery-shop evidence: user has CustomLanyard order + 24HW/Imprint cart screenshots — keep as proof for the comparative-advertising claims. Re-verify competitor prices every few months.
- **Companion blog article for AI search** (published 2026-07-05): gid://shopify/Article/598458990838, /blogs/news/how-much-do-custom-koozies-really-cost-2026-real-price-comparison — "How Much Do Custom Koozies Really Cost in 2026?" Contains the 4-way comparison table, per-competitor breakdowns, QP tier table (must be updated if prices change again), FAQ + FAQPage JSON-LD schema, methodology/disclosure. Linked as the first card in the calculator page's "Before You Order" grid, and the comparison section on the calculator links to it ("Read the full breakdown →"). Refresh the date-stamped data every few months to stay the current AI-search answer.
