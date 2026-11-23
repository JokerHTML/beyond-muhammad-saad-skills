---
name: color-grading
description: Grade every reel identically with one locked ffmpeg-only chain at final encode, verified numerically against signalstats targets — Hald LUT freeze, Rec.709 delivery.
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
sources:
  - FFmpeg filters documentation (curves, signalstats, haldclut, setparams, deband, noise, eq)
  - ffmpeg-cookbook, "Apply 3D LUTs for Color Grading with the lut3d Filter"
  - awesomeskills.dev, "Video Color Grading" (order of operations, ASC CDL model, LUT blending)
  - mcpmarket, "FFmpeg LUT Grade" skill (tetrahedral interpolation, filter stacking)
  - YouTube Help, "Recommended upload encoding settings" (bitrates)
---

# Color Grading System (ffmpeg-only)

## PURPOSE
Grade every reel identically, from one locked chain, verified numerically —
so the brand palette survives platform compression rich instead of washed
out. Palette anchors are CONFIGURATION, not identity: set them once per
series in `grade-config.md` (dark ground hex + its limited-range luma,
light hex + its luma, accent hex + its luma) and never change them mid-series.

**Example anchors** (one series' config, not a rule): dark `#0A0A0C`
(luma ≈10 full / ≈25 limited), light `#F5F2EA` (≈243 / ≈225), accent
`#FFC933` (R at the 255 ceiling; luma ≈202 / ≈189).

## WHEN TO USE
Final encode of every reel in the series. Applies to graphics reels;
face-cam inserts get the §FACE exception only.

## THE ARCHITECTURE (never deviate)
1. **Render clean** — palette-exact frames, ungraded. Grain goes ONLY into
   background layers at render; text layers stay clean.
2. **Assemble losslessly** — `libx264 -crf 0` (or ffv1 for archive). Never
   grade a lossy intermediate.
3. **Grade ONCE, at final encode**, with the master chain below — one
   transform, identical on every frame. Order of operations, always:
   correction (neutral, consistent) → look (this chain) → finishing
   (grain is already in the chain; sharpening last, only if sanctioned).
4. **Verify numerically** (QC gate below) and file the probe output next
   to the encode command.
Photographic inserts that need correction are pre-graded **on the asset
alone** before assembly — never by unlocking the master chain. A look
change = a new LUT version (§LUT) from the next reel, never retro-applied
mid-series.

## THE MASTER CHAIN (series default — the only approved chain)
```
ffmpeg -i assembled_lossless.mp4 \
 -vf "deband=1thr=0.02:2thr=0.02:3thr=0.02:4thr=0.02:range=16:blur=1,noise=alls=5:allf=t+u,curves=master='0/0 0.25/0.21 0.5/0.50 0.75/0.79 0.9/0.87 1/0.94':interp=pchip,eq=saturation=1.00,format=yuv420p,setparams=color_primaries=bt709:color_trc=bt709:colorspace=bt709:range=tv" \
 -c:v libx264 -profile:v high -crf 16 -preset slow \
 -movflags +faststart out_1080x1920.mp4
```
Why each stage exists:
- **deband** (low thresholds only — high values eat thin text strokes):
  replaces banded pixels before the encoder sees them.
- **noise alls=5, allf=t+u:** just enough grain that H.264 cannot collapse
  the near-black ground into macro-block blotches (the real cause of
  "washed out"). There for the encoder, not the viewer — must be invisible
  at phone size. ⚠️ Do NOT use `gradfun` before lossy compression
  [reported in source research, not verified against ffmpeg docs —
  treat as a rule, re-verify before relying on it].
- **curves (master, pchip):** the S-curve — midtone contrast from the
  middle slope; `interp=pchip` because the default spline can overshoot
  and clip. The **0.9/0.87 → 1/0.94 shoulder** caps whites at ~94% so the
  light anchor never hard-clips or merges into a flat block after
  re-encode. Master curve only — per-channel S-curves shift hue in
  saturated areas.
- **eq saturation=1.00:** the palette is already final; saturation is a
  correction here, not a look (working band 0.92–1.05, default 1.00).
  Saturation always sits BEFORE the final shoulder logic — the shoulder
  is the last thing touching channel ceilings.
- **setparams (mandatory, not optional):** the encoder-level flags
  `-color_primaries bt709 -color_trc bt709` are silently dropped by
  ffmpeg 8.1.2 on some builds (verified 2026-11-23: output showed
  `color_primaries=unknown`, failing this skill's own QC gate). The
  `setparams` filter stage is what actually writes all four tags.

## HARD RULES
- **Blacks stay ANCHORED for graphics.** `0/0` — never lift the dark
  ground globally (lifted variant `0/0.05 …` is for photographic looks
  only). "Washed out" is fixed by grain + range tags, never by lifting.
- **Range integrity:** limited/tv in the tag AND in reality. A full-range
  file tagged tv (crush) or limited content tagged pc (wash) = fail,
  re-encode.
- **The accent is never boosted.** An accent with a channel at 255 (e.g.
  `#FFC933`, R at ceiling): any saturation increase clips that channel
  while the others move → hue slides and flat fills posterize. If the
  accent still clips after the chain, the approved fallback is the
  per-channel endpoint pull — `curves=r='0/0 1/0.97':g='0/0 1/0.95':b='0/0
  1/1'` — which REDEFINES the delivered accent and needs one-time human
  approval before becoming the series standard.
- **Vibrance discipline:** pure-graphic reels keep `vibrance` at 0
  (nothing muted to rescue, everything to clip). Mixed/photo reels may
  use `vibrance=intensity=0.10–0.30`. ffmpeg's vibrance selectivity is NOT
  documented as saturation-aware — before relying on it, run the
  palette-strip test (crop accent swatch + muted swatch, compare
  `signalstats` before/after: the accent's SATAVG must move LESS than the
  muted swatch's; equal movement = vibrance buys nothing, use §saturation
  only). Never `alternate=1` (changes hues).
- **Text edges are built in LUMA, not hue (render rule the grade cannot
  fix):** delivery is 4:2:0 — chroma is quarter-resolution, colour-only
  edges smear and no bitrate fixes it. Light-on-dark (ΔY≈233) and
  accent-on-dark (ΔY≈192) are luma edges — safe. **Accent on light
  (ΔY≈41) is FORBIDDEN for small text** — re-render, never re-grade.
  Accent-coloured text strokes ≥3–4px at 1080 wide. Luma-only sharpening
  (`unsharp=5:5:0.3:5:5:0.0`) is the only sanctioned encode-side
  mitigation; skip if it halos.

## THE LUT (series lock)
Once the master chain is approved on a test reel, freeze it into a Hald
CLUT and grade future reels with that single file. The LUT build MUST use
the exact master curve — including the `0.9/0.87` shoulder point. (The
previous version of this skill dropped that point in the build command,
so the frozen LUT was not the curve it claimed to freeze; verified
2026-11-23: corrected LUT sits ΔYAVG 0.34 from the direct chain, the
buggy one ΔYAVG 1.41.)
```
# Build once (curve identical to the master chain, point for point):
ffmpeg -f lavfi -i haldclutsrc=8 -vf "curves=master='0/0 0.25/0.21 0.5/0.50 0.75/0.79 0.9/0.87 1/0.94':interp=pchip,eq=saturation=1.00" -frames:v 1 grade_hald_v1.png
# Apply (lossless intermediates only):
ffmpeg -i in.mp4 -i grade_hald_v1.png -filter_complex "[0][1]haldclut=interp=tetrahedral,setparams=color_primaries=bt709:color_trc=bt709:colorspace=bt709:range=tv" -c:v libx264 -crf 16 -preset slow -movflags +faststart out.mp4
```
- Name + date every LUT version; never edit one in place. LUTs are dumb
  maps (no scene adaptation) that bake in any clipping — that's why the
  chain is approved BEFORE freezing.
- Validate each new LUT on a palette chart: graded swatches must match
  the direct chain within ±1 code value per swatch (sample the flat
  swatch centres, not frame-wide YMAX — grain makes frame-wide extrema
  move by up to ~3). If it fails, regenerate at a larger Hald level
  (`haldclutsrc=10` or `12`).
- No LUT intensity slider exists in lut3d/haldclut. To run a LUT at
  reduced strength, blend graded/ungraded streams deliberately:
  `split[a][b];[b]haldclut=...[g];[a][g]blend=all_expr='A*(1-0.7)+B*0.7'`
  (0.7 = 70% strength). Don't improvise a fade per reel.

## DELIVERY TARGET
Rec.709, 8-bit SDR, H.264, yuv420p, **color_range tv**, all four colour
tags present (YouTube's published guidance; every platform re-encodes,
so the same file defends Instagram). YouTube reference bitrates, SDR
[YouTube Help, recommended upload encoding settings]: 1080p 8 Mbps @30fps
/ 12 Mbps @60fps. An oversize upload master is a SIGNAL-grade tactic —
verify per platform, never promise it as a guarantee.

## FACE EXCEPTION (face-cam inserts only — skip entirely for graphics reels)
Graphics reels have no skin: add NO skin step, and never dull the accent
to solve a problem the reel doesn't have. For face inserts, ffmpeg has no
skin qualifier and no hue-selective tool, so the only defence is order +
restraint: white-balance FIRST with small `colorbalance` moves (±0.05),
saturation LAST and ≤1.05, prefer vibrance over saturation. QC:
`histogram=mode=color2` — the skin cluster's angle must not move between
balanced and final frames; only its distance from centre may change.

## NUMERIC QC GATE (delivery file, every reel — no eyeballing)
```
ffprobe -show_streams out.mp4   # must show bt709 / bt709 / bt709 / color_range=tv — any "unknown" = FAIL
ffmpeg -v info -i out.mp4 -vf "signalstats,metadata=print" -f null - 2>&1 | grep "lavfi.signalstats"
ffmpeg -i out.mp4 -vf "signalstats=stat=brng" -f null -   # out-of-range population must be zero/unexplained-free
```
(Bare `signalstats` logs nothing on ffmpeg 8.x — the `metadata=print`
stage is required to read the values.)

### Reference row — establish yours, then hold it
On the first approved reel, record the frame-averaged values below and
paste them into `grade-config.md` as the series reference row. Never
compare against another series' row: YAVG/SATAVG depend on the frame
content. What travels across series is the SHAPE of the gate, not the numbers.

**Worked example** (measured 2026-11-23, ffmpeg 8.1.2, 2 s palette-chart
clip through the master chain — dark/light/accent blocks + grey ramp +
gradient; 60-frame averages): YMIN 14.7, YLOW 21.0, YAVG 126.8,
YHIGH 213.0, YMAX 224.0, SATAVG 18.1, SATMAX 86.1.

Pass criteria (against YOUR reference row):
- All four colour tags present, `color_range=tv` — any "unknown" = FAIL.
- `YMAX` ≤ ~240 — the shoulder cap; never a hard 255 plateau.
- `YHIGH` measurably below `YMAX` (a gap = shoulder exists; equal =
  clipped plateau = FAIL). Example row: 213 vs 224.
- `YLOW` (10th percentile) within ±5 of the reference row — use YLOW,
  not YMIN: the noise stage makes the single-pixel minimum unstable
  (measured YMIN 14.7 against a dark-anchor expectation of ~25; YLOW
  21.0 is the stable anchor). YMIN is reported, never gated.
- `SATMAX` stable reel-to-reel within a small tolerance; a jump = a
  saturation/LUT fault.
- Accent flat-fill crop = a single tight signalstats cluster (two
  populations = posterization = FAIL).
- Determinism: same test reel through the chain on two builds →
  `YAVG/SATAVG/YLOW/YHIGH` identical within rounding (YMIN/YMAX may
  jitter ±3 from the noise stage — that jitter is expected, not a fault).

## FAILURE MODES
- Washed-out blacks after upload → check range tags first (tagging, not
  grading), then grain presence.
- Banding in gradients → deband thresholds or noise too low; verify on the
  ENCODED file on a non-OLED screen, never the master.
- Accent gone green/pale → a saturation stage ran after (or inside) the
  chain; remove it — the accent is never boosted.
- Haloed text → remove the unsharp stage.
- Tags show `unknown` → the `setparams` stage is missing or placed
  before `format=yuv420p`; it must come after the format conversion.

## STOP CONDITIONS
- Stop and escalate if the QC gate fails twice on the same file — the
  input render is wrong (clipped at render cannot be recovered by any
  grade). Re-render, don't re-grade.
