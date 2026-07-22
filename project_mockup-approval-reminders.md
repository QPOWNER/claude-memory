---
name: mockup-approval-reminders
description: "Flow workflow \"Mockup approval reminder emails\" + Rony's Gmail template — automates customer nudges until mockup approved; 7/22/26 status = 90% built, NOT on, draft needs Discard"
metadata: 
  node_type: memory
  type: project
  originSessionId: 15fa4729-7c4a-43a7-96e3-b4a75ef06f56
---

System (designed 7/22/26): Rony sends mockup from rony-custom@ using a saved **Gmail Template** (source: `C:\Users\qpllc\Documents\QP-Approval-Email\gmail-template-for-rony.html` — bracketed placeholders, drag-in mockup PNG avoids Gmail img-stripping, generic Approve mailto → rony-custom@ cc sales@). He then tags the order **`mockup-sent`** → Flow waits 2d → if no **`approved`** tag AND not cancelled AND unfulfilled → email reminder #1 to customer → 2d → reminder #2 + internal alert to contact@ + rony-custom@. Tag `approved` (added next to mockup-sent, no need to delete) stops everything; remove+re-add `mockup-sent` restarts after a revised mockup. Rony's "Manage order information" permission should allow tagging (untested).

**Key facts learned:**
- Flow has NO native order-tag trigger and its built-in "Send internal email" REFUSES variables in To (can't email customers).
- Installed 7/22/26 (both free tier): **WorkflowMail** (apps.shopify.com/flowmail, 500 lifetime emails, sends from contact@) for customer emails; **Workflow Trigger Extensions** (apps.shopify.com/flow-trigger-extensions, 5k events/mo) for the "Order tags added" trigger. Sendjo was rejected (50-email cap, 0 reviews).
- Workflow ID: admin.shopify.com/store/qualityperfection/apps/flow/editor/019f8a67-d106-7824-aef9-8d6f2b22d152 — saved to store 7/22 11:22 AM, **OFF**.

**REMAINING (workflow is NOT finished):** 1) Open workflow → click **Discard changes** (a Sidekick edit on 7/22 wrecked the draft — trigger became "Order created"; the APPLIED version is the good one; do NOT Apply the draft). 2) Add WorkflowMail "Send transactional email" on first condition's True branch (reminder #1). 3) Replace the leftover Sendjo step with WorkflowMail (reminder #2). 4) Fix internal email recipient staff@example.com → contact@ + rony-custom@. 5) Clear Review flags, Apply, Turn on. Reminder copy drafts are in the 7/22 session transcript.

**Gotchas:** Flow editor canvas ignores synthetic scroll/pan/zoom from claude-in-chrome most of the time (worked once after a fresh reload; node panels open by clicking the node's header icon). Opening a left panel squeezes the canvas and exposes lower nodes. Flow editor tab intermittently freezes the renderer (screenshots time out) — fresh tab helps. Do NOT delegate edits to Shopify Sidekick on an existing workflow — it rebuilds from scratch.

Rony one-time Gmail setup still to do (Settings→Advanced→Templates→Enable; paste template; save as "Mockup Approval"). Related: [[approval-mockup-email]], [[custom-orders-staff-member]], [[customizer-art-pipeline]]
