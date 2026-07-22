---
name: runhong-paypal-invoice-reconciliation
description: How to reconcile Runhong (supplier) PI invoices vs order CSV vs PayPal — billing pattern and verified 7/22/26 status
metadata: 
  node_type: memory
  type: project
  originSessionId: 68805650-917c-4397-a439-0388fd8951a6
---

Koozie supplier Dongguan Runhong (Benson, benson@runhongsports.cn / .com; bills as 潤弘實業（香港）有限公司) bills each Proforma Invoice as a batch of $2,000 PayPal invoices plus ONE final odd-amount invoice equal to the remainder (0305A ended $1,281, 0316A $2,240, 0403A $498). Each PayPal invoice item is named "New Neoprene Koozies <PI#>-<n>" with the PI PDF attached — open payer view at paypal.com/invoice/payerView/details/INV2-... to see which PI it belongs to. PayPal receipts do NOT come to Gmail; check PayPal directly (business account logged in via Chrome).

Status verified 7/22/26 for PI RH20260420A ($34,790.25 = 158 cartons × 480 units, goods $27,129.60 + shipping 158×$38 + 5% PayPal):
- 16 unpaid invoices #0271–#0286 ($32,000) issued 7/22 → final $2,790.25 invoice still expected; don't treat $32k as full settlement.
- CSV order matches invoice 100%; shipments cover 138/158 cartons — 22 cartons never shipped (incl. True Blue 3, stripes colors, Slim USA Flag 2, 16oz 6-colors), and Slim Police + Slim Forest Camo overshipped by 1 carton each.
- PIs 0305A/0316A/0403A fully billed & paid. Foam PIs (0408A, Foam 0420A) not yet billed via PayPal.
- Reading their PI PDFs: text is CID-encoded (char = CID + 29, 0x0003 = space) — decode scripts in scratchpad worked (inflate streams, map glyphs).

The user's order tracking file is "QP Order Systerm 2026.xlsx" (note typo "Systerm") — per-month sheets, col B = order lines, col C = shipment batches with tracking + ETAs; tracking numbers are shared across PIs (one boat shipment can carry cartons from multiple PIs).
