---
name: mockup-approval-reminders
description: "Flow workflow \"Mockup approval reminder emails\" + Rony's Gmail template — automates customer nudges until mockup approved; 7/22/26 late PM status = BUILT, APPLIED, TURNED ON; remaining = Rony Gmail template setup + live test"
metadata: 
  node_type: memory
  type: project
  originSessionId: 15fa4729-7c4a-43a7-96e3-b4a75ef06f56
---

System (designed 7/22/26): Rony sends mockup from rony-custom@ using a saved **Gmail Template** (source: `C:\Users\qpllc\Documents\QP-Approval-Email\gmail-template-for-rony.html` — bracketed placeholders, drag-in mockup PNG avoids Gmail img-stripping, generic Approve mailto → rony-custom@ cc sales@). He then tags the order **`mockup-sent`** → Flow waits 2d → if no **`approved`** tag AND not cancelled AND unfulfilled → email reminder #1 to customer → 2d → reminder #2 + internal alert to contact@ + rony-custom@. Tag `approved` (added next to mockup-sent, no need to delete) stops everything; remove+re-add `mockup-sent` restarts after a revised mockup. Rony's "Manage order information" permission should allow tagging (untested).

**STATUS 7/22/26 ~9:46 PM (desktop session): WORKFLOW FINISHED AND TURNED ON.** Steps done: 1) wrecked Sidekick draft discarded; 2) BOTH leftover dead Sendjo "Send transactional email" steps deleted (Sendjo uninstalled, steps errored); 3) WorkflowMail "Send transactional email" added at reminder-#1 position (cond-2 True → email → reconnected to Wait via drag, which DOES work for connectors even though canvas pan/scroll drags don't); 4) WorkflowMail reminder #2 added on cond-3 True next to internal alert; 5) internal email To: fixed staff@example.com → contact@ + rony-custom@; 6) Apply changes; 7) Turn on workflow — confirmed "Workflow turned on" toast, button now "Turn off workflow".

**Email copy live in the workflow** (both: Customer = order.customer.id, Reply-to = rony-custom@quality-perfection.com, plain-text content, CTA/CC/BCC empty):
- #1 subject: `Reminder: your mockup is waiting for approval - order {{ order.name }}` — friendly nudge, reply APPROVED, ships 3-5 business days after approval, spam-folder hint.
- #2 subject: `Action needed: order {{ order.name }} is on hold until you approve your mockup` — firmer ON-HOLD framing, same instructions.
- Internal alert (unchanged copy): subject `No approval received after 4 days for order {{ order.name }}`, body has order/customer details + admin link.

**Key facts learned:**
- Flow has NO native order-tag trigger and its built-in "Send internal email" REFUSES variables in To (can't email customers).
- Installed 7/22/26 (both free tier): **WorkflowMail** (apps.shopify.com/flowmail, 500 lifetime emails, sends from contact@) for customer emails; **Workflow Trigger Extensions** (apps.shopify.com/flow-trigger-extensions, 5k events/mo) for the "Order tags added" trigger. Sendjo was rejected (50-email cap, 0 reviews) and uninstalled.
- Workflow ID: admin.shopify.com/store/qualityperfection/apps/flow/editor/019f8a67-d106-7824-aef9-8d6f2b22d152 (editor URL needs the draft id appended when a draft exists; bare /editor/<id> 404s — enter via the workflow list or overview page).

**REMAINING:** 1) Rony one-time Gmail setup (Settings→Advanced→Templates→Enable; paste template from the HTML file; save as "Mockup Approval"). 2) Live test: tag a test order `mockup-sent`, confirm reminder #1 lands after 2d (or use Flow "Select test event"), confirm `approved` tag stops the chain. 3) WorkflowMail free tier = 500 lifetime emails — watch usage, upgrade if the flow proves out.

**Gotchas (browser automation):** Flow editor canvas ignores synthetic scroll/pan/zoom AND background drags, but node-to-node CONNECTOR drags work (left_click_drag from output stub to target node). Use the bottom-left zoom-out/fit buttons to see the graph. Panel field edits commit on blur — click another field/canvas before closing a panel or the edit can be lost (bit us once on the internal-email To field: verify after Apply). Deleting a mid-chain step orphans its children (Review flag on them) — reconnect via the parent's output stub. Renderer intermittently freezes on CDP screenshots (fresh tab + reload + 10s waits recover it; clicks still land while frozen). Do NOT delegate edits to Shopify Sidekick on an existing workflow — it rebuilds from scratch.

Related: [[approval-mockup-email]], [[custom-orders-staff-member]], [[customizer-art-pipeline]]
