---
name: mockup-approval-reminders
description: "Flow workflow \"Mockup approval reminder emails\" + Rony's Gmail template — automates customer nudges until mockup approved; 7/22/26 status = 90% built, NOT on, draft needs Discard"
metadata: 
  node_type: memory
  type: project
  originSessionId: 15fa4729-7c4a-43a7-96e3-b4a75ef06f56
  modified: 2026-07-23T12:43:10.003Z
---

System (designed 7/22/26): Rony sends mockup from rony-custom@ using a saved **Gmail Template** (source: `C:\Users\qpllc\Documents\QP-Approval-Email\gmail-template-for-rony.html` — bracketed placeholders, drag-in mockup PNG avoids Gmail img-stripping, generic Approve mailto → rony-custom@ cc sales@). He then tags the order **`mockup-sent`** → Flow waits 2d → if no **`approved`** tag AND not cancelled AND unfulfilled → email reminder #1 to customer → 2d → reminder #2 + internal alert to contact@ + rony-custom@. Tag `approved` (added next to mockup-sent, no need to delete) stops everything; remove+re-add `mockup-sent` restarts after a revised mockup. Rony's "Manage order information" permission should allow tagging (untested).

**Key facts learned:**
- Flow has NO native order-tag trigger and its built-in "Send internal email" REFUSES variables in To (can't email customers).
- Installed 7/22/26 (both free tier): **WorkflowMail** (apps.shopify.com/flowmail, 500 lifetime emails, sends from contact@) for customer emails; **Workflow Trigger Extensions** (apps.shopify.com/flow-trigger-extensions, 5k events/mo) for the "Order tags added" trigger. Sendjo was rejected (50-email cap, 0 reviews).
- Workflow ID: admin.shopify.com/store/qualityperfection/apps/flow/editor/019f8a67-d106-7824-aef9-8d6f2b22d152 — saved to store 7/22 11:22 AM, **OFF**.

**✅ LIVE since 7/22/26 9:46 PM — user finished it from their home computer** (workflow "Mockup approval reminder emails" = Active; visible top: trigger → mockup-sent check → Wait **2 days** → reminder; activation implies all steps validated/linked). Still pending: Rony's one-time Gmail template setup + first real-order test (watch Flow "Recent runs" after Rony's first mockup-sent tag; WorkflowMail dashboard "Sent emails" counts sends). To change reminder delay: edit the Wait step.

**History of the build (7/22, kept for context):** Design changed to DAILY repeat: trigger→cond(mockup-sent)→Wait 1 day→cond(no approved/not cancelled/unfulfilled)→WorkflowMail reminder. User built the WorkflowMail email in a live-guided session (subject "Still waiting on your approval", reply-to rony-custom@, recipient {{ order.email }}, body done) BUT subsequent deletions (2nd wait, internal email, Sendjo2) DETACHED the tail: Apply now fails with "Remove or connect unlinked steps — 4". FIX: in editor, delete all 4 unlinked floater steps (incl. orphaned WorkflowMail email + Remove-order-tags), re-add WorkflowMail "Send transactional email" on the approved-condition's True (+ button), retype subject/body, Apply, Turn on. IMPORTANT LEARNINGS: extension trigger exposes NO native `order` resource → native Add/Remove-order-tags actions error "No order found" and WorkflowMail's Add-variable picker is empty (typed {{ order.name }} rejected — write copy without order number); auto-loop via tag remove/re-add is therefore IMPOSSIBLE — daily "loop" = Rony manually removes+re-adds `mockup-sent` to re-arm; DISCARD would revert to 11:22 AM Sendjo version (also unusable) — don't. Interim routine: Rony uses Gmail Snooze (1 day) on sent mockups and nudges manually.

**Gotchas:** Flow editor canvas ignores synthetic scroll/pan/zoom from claude-in-chrome most of the time (worked once after a fresh reload; node panels open by clicking the node's header icon). Opening a left panel squeezes the canvas and exposes lower nodes. Flow editor tab intermittently freezes the renderer for 30-90s after each interaction and serves STALE frames — clicks land on the real DOM which may differ from the screenshot; NEVER blind-type (7/22: keystrokes hit admin keyboard shortcuts and navigated to Add-blog). drag from a condition's True stub downward DOES open the Action|Condition chooser. Do NOT delegate edits to Shopify Sidekick on an existing workflow — it rebuilds from scratch.

Rony one-time Gmail setup still to do (Settings→Advanced→Templates→Enable; paste template; save as "Mockup Approval"). Related: [[approval-mockup-email]], [[custom-orders-staff-member]], [[customizer-art-pipeline]]
