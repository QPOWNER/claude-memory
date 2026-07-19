---
name: sync-to-drive
description: "At the end of every session, upload new or updated memory and config files to the Google Drive Work folder for cross-machine sync"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: cc4c3d38-e928-4e52-9783-baa9500dad44
---

Always sync memory files to Google Drive at the end of each Claude Code session.

- **Drive folder:** Shared drives > Work > Claude Config (folder ID: 1BmddYuDudrVhAQCesYCTBIvPYXPp8S-h)
- **What to sync:** Any new or updated memory files from `C:\Users\qpllc\.claude\projects\C--Users-qpllc\memory\`
- **Why:** User has two machines (work and home) and wants Claude Code context available at both locations.
- **How to apply:** Before wrapping up a session, check if any memory files were created or changed, and upload them to the Claude Config folder on Drive using the Google Drive MCP create_file tool.
