---
name: youtube-thumbnail-design
description: "Design, render and A/B-test a high-CTR YouTube thumbnail from your artwork and title — a deterministic PIL pipeline (cutout, display type, 3 variants) plus Test & Compare — so the thumbnail earns the click and the watch. For YouTube creators who want thumbnails that test, not guess. YouTube thumbnails only: social-post visuals (carousels, pins, prompt cards) and thumbnail concepts live in carousel-thumbnail-design."
version: 1.1.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
updated: 2026-11-23
sources:
  - YouTube Help, "Add custom video thumbnails" + "A/B test titles & thumbnails" (specs, Test & Compare)
  - vidIQ, "YouTube Thumbnail Design Tips: Best Practices for 2026" (500-video study, Jun 2026)
  - 1of10 >300,000 viral-video study via Search Engine Journal (Dec 2025)
  - ArnavPuri/designskills thumbnail-design (Gemini/HTML path; small-size check)
  - inference-sh/skills youtube-thumbnail-design (120px test, safe zones)
  - charlie947/social-media-skills youtube-thumbnail (brand-config pattern)
  - timscheuerai/content-vault youtube-thumbnail skill (rembg + HTML→PNG)
  - rclonfire/clipforge THUMBNAIL_RESEARCH.md (two-pass OpenCV/Pillow pipeline)
  - jasonc00person/content-os thumbnail skill (never let an image model render text)
  - Joseph19820124/gg-framework youtube-thumbnail-design (evidence hygiene)
---

# YouTube Thumbnail Design

Design, render and test a thumbnail that earns the click AND the watch.
A thumbnail that wins clicks but loses viewers loses the Test & Compare —
the winner is picked by **watch-time share**, not CTR alone.

## 0. Setup (portable — install once, anywhere)

- **Python 3.10+** with a virtual environment:
  `python3 -m venv ~/.venvs/thumbnail && source ~/.venvs/thumbnail/bin/activate`
- **Inside the venv:** `pip install Pillow numpy opencv-python rembg[cpu,cli]`
  (`rembg` downloads its segmentation model on first use, ~170 MB, into
  `~/.u2net/` — allow network on first run; later runs work offline.)
- **Fonts — supply your own, never bundle a licensed one:**
  - Display face: one heavy black display font (see §8 for the licence rule).
    Free OFL fallbacks that work at thumbnail scale: Archivo Black,
    Passion One Black, Bungee, Bowlby One, Anton (all on Google Fonts).
  - Record the exact font file path in your brand config (see below).
- **Brand config** (`brand-kit.md` in the project root — create it before
  the first thumbnail; every later step reads from it, never from memory):
  `display_font_path`, `accent_hex`, `background_hex`, `text_hex`,
  `wordmark_placement`. If it is missing, state the defaults used and get
  them confirmed — never silently invent brand tokens.
- **Brand-token example** (one channel's tokens, not a rule): dark ground
  `#0A0A0C`, gold `#FFC933`, cream `#F5F2EA`, accent yellow `#FFD600`.
  Any palette works if it passes the contrast and chrome-separation
  checks in §3.

## 1. Inputs (gather, don't guess)

- Video title, duration, niche/format (e.g. gaming ranking, 2:47, 16:9).
- Hero asset(s) **as files on disk** — never re-render the hero with a
  generative model (it drifts likeness and hallucinates text); never paste
  chat images.
- Brand tokens from `brand-kit.md` (font path, accent hex, wordmark placement).
- What the video actually contains (count claims, payoff, who is in it) —
  the thumbnail must not claim what the video doesn't show (policy +
  retention). Flag disputed facts as disputed — do not put them on the
  thumbnail.

## 2. Research (before any pixels)

- Live YouTube search for the exact title query; record the top 10
  thumbnails: hook words, count claims, colour, layout, views, age.
- Note the dominant pattern AND the gap (what nobody is doing).
- Evidence baseline [vidIQ 500-video study, Jun 2026]: 69% of breakout
  thumbnails used a face (80% of the biggest overperformers), 56% used
  high-contrast colour, 89% used at least one of the two. Design for a
  small mobile frame first — most watch time is on phones.

## 3. Design rules (hard checklist — fail closed)

- [ ] Build at **3840×2160** (YouTube's recommended size, 2026); export
      **1280×720 JPG** as the upload file. Minimum width 640 px; JPG or
      PNG only. File limit: **2 MB from the mobile app, 50 MB from a
      computer** [YouTube Help, answer/72431, re-read live 23 Nov 2026].
      1280×720 is the Test & Compare floor, not the recommended size — any variant below it drags the whole test
      down to 854×480.
- [ ] Shorts thumbnails: build at **2160×3840** (YouTube's recommended
      Shorts size), 9:16, JPG/PNG, under 50 MB from a computer. Custom
      Shorts thumbnails upload only in Studio on a computer, verified
      account required [YouTube Help, answer/72431, re-read live
      23 Nov 2026]. For Shorts the first frame is the thumbnail in the
      feed until a custom one is set — design frame 1 as the thumbnail.
- [ ] ≤3 elements: subject + 1 context object + 3–5-word text.
- [ ] Text 3–5 words (0–2 can beat 3–5), heavy weight, ≤2 colours, clean
      heavy black stroke (no drop shadow on body text), complements the
      title — **never repeats it**.
- [ ] Face/subject ≥25% of frame (30–50% when a face is the hook);
      eyes in the upper third; never crop through an eye or mouth; eyes
      looking toward the text/subject direct attention.
- [ ] ≤3 colours + black/white; text-to-background contrast ≥4.5:1.
- [ ] Bottom-right (duration stamp) + bottom-left + far edges clear of
      critical text/faces. Keep critical content inside the centre 80%.
- [ ] One emotion, one promise, one visual metaphor.
- [ ] Curiosity gap: shows the consequence, withholds the answer.
- [ ] Honest: no claim the video doesn't deliver; no fake official logo
      lockup; no fake death frame; no mislabelled person; no hard count
      unless the video confirms it.
- [ ] Palette separates from YouTube chrome in light AND dark mode:
      saturated accent on a dark ground (or the reverse). No white-heavy
      or blue-heavy fields.
- [ ] Headline cap-height ≈ 13–16% of image height per line.

## 4. Pipeline (deterministic, in order)

1. **Base:** supplied artwork, cropped tight (hero ≥25% of frame width).
2. **Cutout/enhance (only if the design needs a cutout):** `rembg`
   (`u2net_human_seg` for people) → CLAHE (clipLimit 2.5, 8×8) →
   saturation 1.2–1.4× → unsharp mask → background darkened/desaturated
   60–80% behind the text zone.
3. **Compose:** rule-of-thirds grid; subject off-centre; negative space
   for type; dark gradient panel (60–70% black, feathered) behind text —
   never a solid box unless the design demands it.
4. **Type (PIL only — NEVER model-rendered text):** display font, white
   fill, heavy black stroke, thin accent edge; accent word in the accent
   hex; size ~0.16 image height. Lowercase display type only if that is
   the brand's locked wordmark style — otherwise use the font's normal case.
5. **Export:** 1280×720 JPG (quality 90–92, sRGB) + PNG master at build
   size; record the recipe + provenance (source files, font, crop
   coordinates) in a `thumbnail-recipe.md` next to the output.

## 5. Verification (gate before publish)

- [ ] 320×180 test: mood + subject + text all readable.
- [ ] 120 px test: same, in a feed mock alongside 3 real competitors —
      distinguishable in <1 s.
- [ ] 5-question pre-flight: 1-second comprehension; emotion clear at
      320×180; exactly 3 elements; text ≠ title; palette separates from
      chrome. ≥4/5 yes to ship.
- [ ] Full-size visual read: every word spelled correctly, no cut-off
      text, no face cropped mid-feature, nothing in the duration-stamp corner.
- [ ] File check: exactly 1280×720, sRGB, JPG within the upload limit
      for the upload route (2 MB mobile / 50 MB desktop).

## 6. Variants + testing

- Produce exactly **3 meaningfully different variants** (change ONE element
  each: hero, hook words, or background) in a manifest; human reviews the
  manifest before any render/spend.
- Upload to YouTube Studio **Test & Compare** (up to 3, desktop Studio
  only, advanced features enabled); upload the safe default FIRST — with
  no clear winner YouTube keeps the first upload. Winner = watch-time
  share, not CTR alone; run days to 2 weeks; log CTR at 48 h + retention.
- CTR bands [creator-guide consensus, not a YouTube-published benchmark]:
  <2% rework packaging; 2–4% below average; 4–8% healthy; >8% strong.

## 7. Evidence hygiene

- Tag every number with provenance: [YouTube Help] / [vidIQ 500-video
  study] / [1of10 300K-video study] / [vendor claim] / [estimate].
- When sources disagree (e.g. faces help vs faces neutral), report the
  disagreement — don't pick one silently. Never quote a vendor CTR lift
  as fact.
- Vendor A/B figures (+37%, +154% etc.) are self-reported with no
  auditable methodology — directional only, never factual.

## 8. Licence notes (display fonts)

- A display font is licensed, not owned, unless it states an open licence
  (e.g. SIL OFL). Check the licence before first use.
- Do NOT redistribute, embed, or bundle a non-OFL font file (no repo, no
  template, no webfont). Each user needs their own copy from the foundry
  or its authorised distributor.
- Do NOT download fonts from repos that bundle the font file —
  redistribution likely breaches the EULA. Canonical sources only:
  the foundry site or Google Fonts (for OFL faces).
- Example [Pricedown Black, Typodermic Desktop Licence]: free for
  **finished** static artwork (thumbnails, rendered video) — NOT open
  source. Do not redistribute the `.otf`; get it from
  https://www.dafont.com/pricedown.font or
  https://typodermicfonts.com/pricedown/. A "VI"-style numeral lockup is
  custom artwork, not a font — use Archivo Black as the free match, and
  never present a fan-made lockup as the official logo.

## Changelog

- **v1.1.0 — 2026-11-23 (Round 2):** Renamed `thumbnail-design` →
  `youtube-thumbnail-design` (clearer, matches the repo's YouTube-skill
  naming). Added the Shorts thumbnail spec (2160×3840, 9:16, Studio-on-
  computer only, verified account) — it was missing entirely. Thumbnail
  specs re-verified live against YouTube Help answer/72431 (23 Nov 2026):
  3840×2160 / 2 MB mobile / 50 MB desktop confirmed. Test & Compare
  floor corrected to the precise 854×480. Re-tested the pipeline on a
  fresh synthetic hero (see TEST-LOG.md).
