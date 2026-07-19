---
name: sync-to-github
description: "At the end of every session, commit and push memory files to the private GitHub repo QPOWNER/claude-memory for cross-machine sync (replaced Google Drive sync 7/19/26)"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: e32ceac6-8a58-481a-95cc-17ccf6c21b24
---

Always sync memory files to GitHub at the end of each Claude Code session.

- **Repo:** https://github.com/QPOWNER/claude-memory (private, owner QPOWNER)
- **Local repo:** `C:\Users\qpllc\.claude\projects\C--Users-qpllc\memory\` is a git repo, remote `origin`, branch `main`
- **Why:** User has two machines (work and home) and wants Claude Code context available at both. GitHub replaced the old Google Drive sync (Shared drives > Work > Claude Config) on 7/19/26 per user's choice — do NOT upload to Drive anymore.
- **How to apply:** Before wrapping up a session, if any memory files changed: `git add -A; git commit -m "<summary>"; git push` in the memory folder. Auth is stored via Git Credential Manager (one-time browser sign-in done 7/19/26) — push works non-interactively.
- **On the other machine:** first use requires `git clone https://github.com/QPOWNER/claude-memory.git` into its memory folder (merge carefully — see [[customizer-art-pipeline]] history of the two machines clobbering each other; pull before editing).
