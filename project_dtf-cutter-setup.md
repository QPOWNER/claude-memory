---
name: dtf-cutter-setup
description: "GCC Expert II LX vinyl cutter cuts DTF sheets into 3\" squares via raw HPGL — script, printer queue, and dialed-in settings"
metadata: 
  node_type: memory
  type: project
  originSessionId: 289f9b29-ee84-407a-a3f0-8d2a0bf9c61a
---

Set up 7/19/26: GCC Expert II LX cuts the user's daily DTF sheets into squares with no GCC software (that lives on a different PC).

- Windows printer queue **"GCC-Cutter"** (Generic / Text Only driver, port USB002) sends raw HPGL to the cutter.
- Script: `powershell -File Documents\DTF-Cutter\cut-grid.ps1 -Cols X -Rows Y` — generates an HPGL grid and sends it via winspool RAW. `-DryRun` previews without cutting.
- Dialed-in defaults (verified by test cut): 3"×3" squares, 0.25" gap, 0.25" margin, Force 200g (FS200 works on this machine; max ~350).
- Coordinate convention in script: X = media feed direction (rows), Y = across carriage (cols); 1016 HPGL units/inch.
- Cutter is blind (no registration marks yet) — user jogs blade to first print corner and sets origin on the panel per sheet. The LX has an AAS optical sensor if mark-based contour alignment is ever needed (requires printing L-marks on gang sheets).
- As of setup, user hadn't yet given full-sheet cols×rows for the one-line daily command.
