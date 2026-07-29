---
name: claude-history-github-backup
description: Session transcripts are archived to the private repo QPOWNER/claude-history-backup via a local staging repo; refresh by re-copying and pushing
metadata: 
  node_type: memory
  type: project
  originSessionId: bd9fb987-0d44-4f2b-8f26-57a90c30c309
---

Claude Code **conversation transcripts** are archived to the private GitHub repo `QPOWNER/claude-history-backup` (first backup 7/26/26). This is the one-way transcript archive; [[sync-to-github]] covers `claude-memory`, the two-way memory sync — don't confuse the two.

- Local staging repo: `C:\Users\qpllc\claude-history-backup` (git, branch `main`, tracks origin)
- Source of truth: `C:\Users\qpllc\.claude\projects\` (live history — never modify)
- GitHub CLI at `C:\Program Files\GitHub CLI\gh.exe` (**not on PATH** — use the full path), authenticated as **QPOWNER** via keyring.
- User runs Claude Code only through the desktop app (Microsoft Store); there is no standalone `claude` CLI on PATH. Usual working folder is `C:\Users\qpllc`, so most history lives under project `C--Users-qpllc`.

**To refresh:** robocopy `C:\Users\qpllc\.claude\projects` → `C:\Users\qpllc\claude-history-backup\projects` (`/E`), **delete any nested `.git`** inside the copy (the `C--Users-qpllc\memory` folder is itself a git repo and an embedded repo breaks the commit), then `git add -A`, commit, push. Use `/E` not `/MIR` so the archive keeps transcripts that were later deleted locally.

**Two project folders exist:** sessions launched from `C:\Users\qpllc\.claude` land in project `C--Users-qpllc--claude`, whose memory folder is deliberately near-empty — the real knowledge base is THIS folder (`C--Users-qpllc\memory`), which is the synced repo and is not visible from those sessions. Write new memories here, not there.
