---
name: dtf-gang-sheet-builder
description: Local web app at C:\Users\qpllc\dtf-gang-sheet-builder that builds DTF gang sheets with GCC AAS registration marks (print PNG + cut SVG/DXF); AAS calibration test still pending
metadata: 
  node_type: memory
  type: project
  originSessionId: 0df467bc-ef62-42b8-8722-a029d9dd4cec
---

User runs a DTF transfer business. They buy printed DTF rolls (22-23" wide, 240-360" long) from a 3rd-party gang sheet printer (e.g. dtfnj.com) and cut them on a **GCC Expert II LX** vinyl cutter with AAS II optical registration. Problem: 3rd-party rolls only had a QR code, no registration marks, so the cutter couldn't locate images.

Solution built (July 2026): **DTF Gang Sheet Builder** at `C:\Users\qpllc\dtf-gang-sheet-builder` — Node.js (express/sharp/multer/archiver) local web app, launched via `run.bat`, serves at http://localhost:3377. User uploads images + quantities; app lays them in a grid of 3x3"/3x4" squares, auto-places GCC AAS marks (10mm black squares: 4 corners + segment pairs every 20"), exports ZIP: print-file.png (300 DPI, transparent bg — uploaded to the printer's "upload your own gang sheet" option, printed at 100% scale) + cut-file.svg/.dxf (matching squares for GreatCut/GCC software).

Verified: 360" sheet at 300 DPI renders in ~108s. There is a launch.json entry "gang-sheet-builder" (port 3377) in both `C:\Users\qpllc\.claude\launch.json` and `C:\Users\qpllc\.claude\.claude\launch.json`.

**Still pending when user returns:** one-time AAS calibration test on a short printed sheet (12-24") before ordering long rolls.

Related: [[dtf-cutter-setup]] (the cut-grid.ps1 / "GCC-Cutter" raw queue route for cutting DTF into 3" squares, Force 200), [[image-format-conversion]] (same sharp toolchain).
