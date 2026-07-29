---
name: image-format-conversion
description: "Converting webp/avif design files to PNG on this PC: no ImageMagick/ffmpeg/Python and Windows can't decode AVIF — use node+sharp; `_small` downloads are 85x100 thumbnails, drop the suffix for the 1148x1344 original"
metadata: 
  node_type: memory
  type: project
---

Converting downloaded design files (webp/avif → PNG) on this PC, verified 7/27/26.

**What is NOT available (don't waste turns trying):**
- `magick` (ImageMagick) and `ffmpeg` — not installed, not on PATH.
- `python` resolves to the **Microsoft Store stub** (`WindowsApps\python.exe`) and errors "Python was not found" — there is no real Python (consistent with [[customer-sources-spreadsheet]]).
- Windows' own imaging stack (WIC via .NET `BitmapDecoder`) **cannot decode AVIF** — fails `0xC00D5212` "No suitable transform"; the AV1 Video Extension isn't installed. It reads webp fine.

**What works:** Node v24 (`C:\Program Files\nodejs\node.exe`) + **sharp**. `npm install sharp` takes ~3s (5 packages). sharp decodes webp AND avif (it reports avif as format `heif`) and writes PNG with alpha preserved. Install it in the session scratchpad, not in a project folder. Same sharp used by [[customizer-art-pipeline]] and [[qp-font-catalog-codes]].

**The `_small` thumbnail trap:** the site these design files come from serves two files under the same hash name — `<hash>_small.webp/avif` is only **85x100** (a few KB), while `<hash>.webp` is the real **1148x1344**. Downloading the `_small` one and converting gives a useless postage stamp; upscaling can't recover it. **Always check pixel dimensions before converting, and re-download without the `_small` suffix** (or look in Downloads — the full-size version is often already there from an earlier day).

**Don't trust filenames or file sizes to tell variants apart** — three "Hoosier bison" files were all 1125x1200 but pixel-different (different quote-text layouts). Compare decoded pixels (sharp `.raw()` → sha256) to know what you actually have. Also note a PNG converted from a **lossy** webp is no better than the webp; if an original PNG exists, print from that.

Finished PNGs go directly in the Downloads root, per [[qp-font-catalog-codes]]. Converted 7/27/26: `alaska-2026.png` and `kierans-1st-birthday.png` (both 1148x1344, transparent) and `hoosier-bison-quote.png` (1125x1200, **solid crimson background — no transparency**, so it won't drop onto another garment color).
