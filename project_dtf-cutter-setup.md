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
- 7/19/26: stock 45° blade only cut through in one direction (dragging, snagged a sheet). User ordered from vinylcutterparts.com (~$66 w/ $12 ship): GCC Green Cap 60° 2.5mm blades + cutting strip. WAITING FOR DELIVERY — when it arrives: install strip + 60° blade (tip out ~credit-card thickness), then send test grid and re-tune force (expect below 250g, was FS250+VS20 on last test).
- Blade fit warning: Expert II takes 2.5mm blades; Amazon multipacks are 2.0mm Roland-type mislabeled as GCC — don't buy those. HPN green cap out of stock 7/19/26.
- Market research done 7/19/26: no auto DTF sheet cutter exists between ~$2k (hand-fed vinyl cutters) and ~$12k (Neolt XY / camera flatbeds, e.g. Printomize $11,995) — user's patent idea targets this gap; user asked for patent-landscape research as possible next step.
