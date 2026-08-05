---
name: customer-buyer-tags
description: Customers tagged blank-buyer / custom-buyer with matching segments (8/5/26) so email campaigns can target blank-koozie businesses vs customizer customers
metadata:
  node_type: memory
  type: project
---

8/5/26 — user asked to separate "custom" vs "regular" customers for email targeting (follow-up to [[customer-business-directory]] launch email).

**FINAL DESIGN — purchase-based segments (auto-update, no mass tagging needed):**
- "Custom-print buyers" gid://shopify/Segment/561911529718 (22 members) — `customer_tags CONTAINS 'custom-buyer' OR products_purchased(id: (15 numeric product ids)) = true`
- "Blank buyers (regular customers)" gid://shopify/Segment/561911496950 (4,522) — `number_of_orders > 0 AND customer_tags NOT CONTAINS 'custom-buyer' AND products_purchased(...) = false`
- The 15 custom products = Personalized* + Design Recreation ×2 + Expedited Printing (ids in segment query; segmentation needs NUMERIC ids, not gids). **When a new Personalized product is created, add its id to BOTH segment queries** (segmentUpdate). 9 of the 22 custom buyers are tag-only (bought custom via deleted products / mockup-tagged orders — products_purchased can't see those).
- Only the 22 `custom-buyer` tags exist (applied via MCP aliased tagsAdd). Tag new manual/custom-quote customers `custom-buyer` to route them correctly; 4 both-type customers count as custom only.
- 7,866 orders → 4,544 customers with orders (analysis via bulkOperationRunQuery → classify.js in session 8ec611bc scratchpad).

**Pipeline gotchas:** MCP blocks bulkOperationRunMutation; `shopify store execute` runs it BUT its token LACKS write_customers — all 4,526 tagsAdd rows failed ACCESS_DENIED while the op reported COMPLETED/no errorCode (per-row errors only in the result JSONL — always download & check it). Each API client sees only its own bulk ops. MCP client CAN tagsAdd (aliased batches OK, ~10 cost each).

**Shopify Messaging campaign gotchas (from building the directory email in admin browser):** editor is an iframe — a11y tree/read_page sees nothing, coordinate clicks only; single clicks often don't focus fields → double-click and VERIFY focus ring via screenshot BEFORE typing (typed text otherwise leaks into admin as keyboard shortcuts and navigates away — happened 3×, once to Settings→Users); URL field: type URL then ArrowDown+Enter to commit suggestion (field then shows value); rich text: select section via ?section= URL param, click text, ctrl+a works INSIDE focused editable only.
