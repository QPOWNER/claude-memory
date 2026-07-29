---
name: qp-tools-repo
description: "Private repo QPOWNER/qp-tools backs up the five custom tools (gang sheet builder, profit dashboard, site scanner, koozie app, approval email) so they exist off this PC and clone onto the second machine; staged copy at C:\\Users\\qpllc\\qp-tools"
metadata: 
  node_type: memory
  type: project
---

The custom tools used to live **only** on this PC (none were on GitHub; only QP-Profit-Dashboard was even a local git repo, with no remote) — a real risk given the confirmed hardware fault in [[pc-black-screen-issue]]. Fixed 7/29/26: private repo **`QPOWNER/qp-tools`**, one repo with each tool as a subfolder.

- Staging repo: `C:\Users\qpllc\qp-tools` (git, `main`, tracks origin; identity set locally = Quality Perfection / contact@). 132 files, ~5 MB.
- Contents: `dtf-gang-sheet-builder/` ([[dtf-gang-sheet-builder]]), `QP-Profit-Dashboard/` ([[qp-profit-dashboard]]), `QP-Site-Scanner/` ([[qp-site-scanner]]), `koozie-customizer-app/` ([[koozie-customizer-app]]), `QP-Approval-Email/` ([[approval-mockup-email]]).
- **Excluded on purpose:** `node_modules` (run `npm install`), `build/`, `.shopify/`, `.vscode/`, and **`.env`** — the koozie app's `.env` holds live `SHOPIFY_API_KEY`/`SHOPIFY_API_SECRET`, so a `.env.example` is committed instead (force-added: the Shopify app's own nested `.gitignore` ignores `.env.*`).
- **NOT backed up anywhere:** `Documents\QP-Customizer-Art` — ~17 GB / 3,686 files, too big for git. Still single-copy on this PC; needs an external drive or cloud storage. See [[customizer-art-pipeline]].
- Dashboard data was checked before pushing: no customer PII (no emails/addresses/phones) and the sample orders are demo rows.

**It is a COPY, not the working folder.** The tools still run from their original paths (`C:\Users\qpllc\dtf-gang-sheet-builder`, `C:\Users\qpllc\Documents\<tool>`). Edits there do NOT reach the repo — re-copy (robocopy `/E` with `/XD node_modules .git build dist .shopify .cache .vscode /XF .env`), then commit and push. QP-Profit-Dashboard's old local history was not carried over.

**On the other machine:** `git clone https://github.com/QPOWNER/qp-tools.git`, then `npm install` per tool, and for the koozie app copy `.env.example` → `.env` with real Partner-dashboard credentials. Note this repo holds **code only** — [[sync-to-github]] (`claude-memory`) syncs the memory notes, and neither repo carries the art library.
