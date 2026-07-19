---
name: draft-order-from-quote-request
description: "When user asks for a draft order from a custom koozie quote request, pull the latest Tally submission from Gmail and create a Shopify draft order"
metadata: 
  node_type: memory
  type: project
  originSessionId: 10c297ad-4eff-4b38-a4b2-b50a9f04488a
---

User's standing workflow (est. 2026-07-05): when they say "make a draft order for the latest quote request" (or similar), do this:

1. Search Gmail (contact@quality-perfection.com) for the newest Tally notification email for the form "Custom Koozie© Quote Request" (form ID D4y7yN).
2. Extract: customer name, email, phone, uploaded file links, and the hidden `quote` field — it contains the full calculator quote (sleeve type, colors, quantity, $/unit, total, rush +$35, design recreation +$10, shipping note). The form has NO standalone quantity field; quantity is inside the quote text.
3. Create a Shopify draft order via graphql_mutation `draftOrderCreate`: custom line item describing the koozies at the quoted unit price × quantity, separate custom lines for rush/recreation fees if present, customer email attached. Orders $45+ ship free (UPS Ground).
4. Do NOT send the invoice automatically — user reviews in Shopify admin and sends it after mockup approval.

Quote requests originate from the pricing calculator page [[koozie-pricing-calculator-page]] which embeds the Tally form and passes the quote via URL param into the form's hidden `quote` field.
