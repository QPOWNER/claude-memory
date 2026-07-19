---
name: qp-font-catalog-codes
description: How to decode QP font/monogram codes like 9-B-QP on order specs — catalog lives in qp-customizer.js QPF_MANIFEST; woff2 downloadable from theme CDN t/38
metadata: 
  node_type: memory
  type: project
  originSessionId: a2b1a8ae-981a-42f3-9e62-b59c94292b9c
---

Order specs use printed-chart codes `N-<FAM>-QP` (regex `^(\d{1,3})-(MS|FS|B|F|W|R|CO|CL|T)-QP$` in qp-customizer.js). Font families: MS=Modern Script, FS=Formal Script, B=Block, F=Fun, W=Western, R=Retro; monogram families: CO, CL, T (+W wreath). The full 115-font catalog is the `/*QPF_MANIFEST*/` array in `Documents\QP-Customizer-Art\theme-push\assets\qp-customizer.js` — entries `[name, woff2, printFileName, family]`. Font files download from `https://www.quality-perfection.com/cdn/shop/t/38/assets/<woff2>`.

**7/14/26: 9-B-QP mapped to LEMON MILK Bold** = 9th Block font in manifest (alphabetical) order, used for the #TooTurntChris proof (Downloads\TooTurntChris-BeachDay2026). CAVEAT: printed-chart numbering vs manifest order is an ASSUMPTION not yet confirmed by the user — verify against the physical chart; update this note once confirmed or corrected.

**7/19/26: chart numbering ≠ manifest alphabetical order.** User called **7-B-QP "Varsity"** → font = **Varsity Team** (`qpf-varsity-team.woff2`, family B), which is 21st alphabetically — so the printed FONTS chart has its own numbering. The 9-B-QP=LEMON MILK mapping above is therefore doubtful too. When an order spec gives a font code, ask/confirm the font NAME (user usually supplies it, e.g. "Varsity font 7-B-QP") and match the name against QPF_MANIFEST instead of relying on position.

**7/14/26: the printed MONOGRAMS & NAMES chart is downloadable** — Shopify CDN files `WEDDING_MONOGRAMS_PAGE-01.jpg` (CO 1-37, CL 1-11, W 1-10, T 1-9, UG 1-3) and `WEDDING_MONOGRAMS_PAGE-02_3a8ee5b2-b72a-4416-9d7e-4f28908a4fba.jpg` (WD 1-46 wedding designs, AL 1-26 alphabet) under `cdn.shopify.com/s/files/1/0514/3566/7652/files/` — codes appear under each design; READ THE CHART IMAGE to resolve any monogram/design code (families WD/UG/AL exist only on the chart, not in the customizer regex). 29-WD-QP done for "The Chappells" 8/1/26 brown #6B4226: script = **Autography** (qpf-autography.woff2), sub line = Playfair Display letterspaced caps (Google Fonts; user wanted 700 weight, month scaled 0.528/0.71 to match Playfair's shorter oldstyle digits). A separate FONTS chart (numbered font families MS/FS/B/F/W/R) was NOT found on the store — still unverified for font codes like 9-B-QP.

**How to apply:** for "make designs" order specs (Side 1/Side 2/Font/Ink), render text→SVG paths with fontkit + sharp in scratchpad (`make_designs.js` pattern, no Python on this PC), 1125px wide ≈ 3.75" @300dpi, transparent PNG per side + Proof-Sheet.jpg. **Save final PNGs directly in Downloads root (user can't find files in subfolders)** — keep working files/SVG in a subfolder if needed. "Ink: Black" → make a grayscale variant of any photo side too. Related: [[customizer-art-pipeline]].
