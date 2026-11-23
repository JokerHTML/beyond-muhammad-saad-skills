---
name: carousel-thumbnail-design
description: "Design mobile-first Instagram carousels, Pinterest pins, LinkedIn document carousels and prompt cards that read at a glance on a phone — layout patterns, type tokens and a 15-point pre-publish gate for creators and designers briefing social visuals. Social-post design only: it briefs layouts and checks them, and hands YouTube thumbnail renders to youtube-thumbnail-design."
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
sources:
  - Instagram Help Centre + gridstats.io carousel measurements (17 Nov 2026): 1080x1350, up to 20 slides, 3:4 grid crop
  - Pinterest Help, "Review ad specs" + Pin specs (read Oct–Nov 2026): 1000x1500 2:3, 20 MB web / 32 MB app, description 800 chars
  - LinkedIn Help, document posts (via Nov 2026 guides): PDF, 100 MB, 300 pages, title required
  - WCAG 2.1 Success Criterion 1.4.3 (contrast 4.5:1 normal text, 3:1 large text)
  - social-media-skills/instagram-carousel-skill (MIT): 10 covers, JSON spec + PIL renderer, slide-type warnings
  - sergebulaev/instagram-skills, Carousel Planner: hook slide, front-loaded value, payoff slide
  - skillsdirectory.com, instagram-carousel (Grade A): swipe-funnel slide roles, save slide
  - Frank Heijdenrijk, "How to Make Instagram Carousels People Save" (Oct 2026): type sizes at 1080px, slide-2 re-show
---

# Carousel, Thumbnail & Visual Design

Design social visuals that are readable at a glance on a phone: carousels,
prompt cards, pin visuals, and thumbnail *concepts* for social posts. It
covers the brief, the layout, the type scale, the pre-publish gate, and the
weekly research habit that keeps the work fresh.

Who it is for: anyone who briefs or checks visuals for social posts — a
designer, a creator, or an agent writing visual briefs for an
image-generation step. This skill writes briefs and checks layouts; it does
not generate images. You supply your own image tool.

## Evidence labels — read before quoting anything

- **FACT** — a platform's own help text, or a measurement you can repeat.
- **REPORTED** — a named study or guide, with date and caveats. Observational,
  not an experiment.
- **Recommendation** — a working rule derived from the evidence, not evidence
  itself. Nothing in this skill invents a number: if a figure would strengthen
  a line and you do not have one, write the line without it.

## Boundary — this skill vs youtube-thumbnail-design

These are two distinct skills with distinct jobs. Do not merge them.

- **This skill (carousel-thumbnail-design)** — the *social-post* design
  skill. It plans, briefs, and checks multi-slide carousels, prompt cards,
  pin visuals, standalone feed visuals, and LinkedIn document carousels, and
  it briefs thumbnail *concepts* (three concepts → one layout spec) for a
  social post. It never renders a finished thumbnail file.
- **youtube-thumbnail-design** — the *YouTube thumbnail* skill. It renders a finished
  1280×720 thumbnail file from supplied artwork through a deterministic PIL
  pipeline (cutout, display type, 3 variants) and tests it in YouTube Studio
  Test & Compare. Use it whenever the deliverable is a YouTube thumbnail
  file. Use this skill whenever the deliverable is a social visual or a
  thumbnail brief.

When a YouTube video needs both: brief the concept here, then hand the chosen
layout spec to `youtube-thumbnail-design` for the render. When a social post needs a
cover image, stay here — do not open the YouTube render pipeline for it.

## Prerequisites

- An image-generation or design tool (any tool that takes a brief and returns an image).
- A way to view images at full size and at phone (stamp) size.
- A contrast checker (any WCAG contrast tool) for the text/background pairs you use.
- A facts source for your post: every number or claim that appears on a visual must come
  from it (see "Canonical-facts lock" below).

## The design system (example — substitute your own)

The palette and type choices below are one worked example system, a dark editorial look.
They are the default in the examples only. Pick your own palette and fonts; keep the
structure (one dark ground, one light text colour, one accent) and keep the contrast rule.

- **Example palette:** near-black `#0A0A0C` (ground) · warm yellow `#FFC933` (accent) ·
  cream `#F5F2EA` (main text) · one restrained grey for secondary text.
- **Example type:** one condensed display face for headlines, one clean sans for body.
  Never more than two typefaces on one visual.
- **Per-post theme varies inside the system:** same colour family, different layout, accent
  balance, imagery, and composition per post. Two near-identical visuals in one day is a
  defect — a viewer scrolling should be able to tell them apart at a glance.

## Hard rules

- **Never big text + empty background + button.** Every visual carries hook + visual story
  + information + proof + hierarchy + brand. A headline floating on a flat field with a
  button is not a design.
- **Real interfaces only.** Show the actual product, tool, or screen the post is about.
  No fake app screenshots, no generic robot stock art, no random neon effects, no
  decorative motion without meaning.
- **Thumbnail promise matches the content.** A thumbnail that promises something the
  content does not deliver is a critical failure. Never use a deceptive thumbnail.
- **Contrast:** text meets WCAG 2.1 Level AA — at least **4.5:1 for normal text and 3:1
  for large text** (Success Criterion 1.4.3). Check every text/background pair with a
  tool; do not eyeball it. **Accent on light fails:** in the example system, yellow
  `#FFC933` on cream `#F5F2EA` measures 1.37:1 — never place the accent on the light
  text colour. Accent goes on the dark ground only (yellow on `#0A0A0C` measures
  12.86:1; cream on `#0A0A0C` measures 17.68:1 — both pass).
- **Safe zones respected.** Keep all text well inside the frame on every side. Text that
  touches, crosses, or runs off any edge is a defect — rebuild, never ship.
- **Alt text for every meaningful image.** Write one plain sentence describing what the
  image shows and what it means.
- **No unreadable tiny text.** If a word cannot be read at phone size, cut it or make it
  bigger. Never shrink a prompt or a block of text to squeeze it beside other content.
- **Text is built in luma, not hue, at small sizes.** On 4:2:0 video and compressed images,
  colour-only edges smear. Small text needs a strong brightness difference from its
  background, not just a different colour.
- **Every visual gets a full text scan before it ships** — read every word on the image
  against the brief, one by one. Any typo, wrong word, duplicated word, or cut-off text
  means the visual is corrected (regenerated or rebuilt) before the post goes out.

## Dimensions (exact — check before export)

| Format | Size (px) | Notes |
|---|---|---|
| Carousel (portrait) | 1080 x 1350 | Up to 20 slides (FACT); 7–10 recommended — 7–12 for save-worthy reference posts; slide 2 is the second hook |
| Pin | 1000 x 1500 | Exact 2:3 — do not ship another ratio; PNG or JPEG, ≤20 MB on the web, ≤32 MB in the app; description ≤800 chars (FACT, Pinterest Help) |
| Shorts / story cover | 1080 x 1920 | 9:16 |
| Standalone feed visual | 1080 x 1350 | Same as carousel slide |
| Document carousel / PDF | 1080 x 1350 per page | LinkedIn document post: one PDF, ≤100 MB, ≤300 pages, every page the same size, document title required (REPORTED, LinkedIn Help via Nov 2026 guides). First page carries the hook. |

Grid-preview warning (REPORTED, measured 17 Nov 2026): a 4:5 slide is shown
cropped to 3:4 on the profile grid, losing about 34 px on each side, with the
carousel icon covering the top-right corner. Keep the cover's key words and
focal image inside the centre — never let a headline touch the left or right
edge. All slides in a carousel share the first slide's ratio: Instagram crops
later slides to match slide 1, so pick the ratio before designing slide 1.

## The 15-point visual gate (hard gate)

One FAIL = revise, never ship. Check every visual against all 15 before it goes out.

1. **Hook at a glance.** A viewer understands the point in under 2 seconds.
2. **Hook + visual story + information + proof + hierarchy + brand** are all present —
   not just a headline on a flat field.
3. **Real subject.** The visual shows the real product, tool, screen, or result — no fake
   screenshots, no generic stock art.
4. **Thumbnail promise matches the content.** Nothing promised that the post does not deliver.
5. **Contrast passes WCAG AA** (4.5:1 normal text, 3:1 large text), checked with a tool.
6. **Safe zones.** All text well inside the frame on every side.
7. **Full text scan passed.** Every word on the image read against the brief; no typo,
   wrong word, duplicate, or cut-off text.
8. **Numbers and claims match the facts lock.** Every figure on the visual is identical
   to the entry in your canonical-facts file (see below).
9. **No ghost words.** No faint, half-formed, or unreadable pseudo-text anywhere on the
   image (see "Ghost-word discipline").
10. **Slide 2 is a second hook** (carousels). The carousel does not go quiet after the cover.
11. **Ranking cards carry all six elements** (when the post ranks things): ranking badge ·
    name · "best for" · key benefit · limitation · where-to-find-it cue.
12. **Prompt cards are readable.** A prompt appears as a clean, readable code-style block
    or prompt card, at a size a phone reader can actually read. Never shrunk to fit.
13. **Alt text written.** One plain sentence per meaningful image.
14. **Dimensions exact.** The exported file matches the size in the table above.
15. **Theme is distinct from the last visual.** Same system, different layout, accent
    balance, and composition — not a near-copy of yesterday's post.

Record one gate line per visual (e.g. `VISUAL-GATE: 15/15 PASS`) in the file where you
keep the post copy.

## Visual brief format

Every brief carries all eight fields. A brief missing one is incomplete — do not send it
to the image step.

1. **Theme name** — unique per post, one short phrase.
2. **Layout sketch** — slide-by-slide for carousels (see patterns below), or a single
   layout description for a standalone visual.
3. **Palette balance** — which colour dominates, which accents, and where.
4. **Headline text** — 3–8 words, hook at a glance, written verbatim.
5. **Proof element** — the real UI, screenshot, chart, or result the visual shows.
6. **Text density check** — word count per slide and the smallest text size used.
7. **Dimensions** — from the table above.
8. **Alt text** — the sentence you will publish with the image.

### Filled-in example brief (Pattern A — listicle / ranking)

Illustrative, written for this skill. A fictional listicle post — no real
product, brand, or performance figure is involved.

- **Theme name:** "Five quiet tools" — one accent colour per slide, same dark ground.
- **Layout sketch (slide by slide):**
  - Slide 1 (cover): headline "5 tools that save an hour a day" top third, large; one
    focal image (a desk with a laptop showing a real tool dashboard) bottom two-thirds.
  - Slide 2 (second hook): "The one most people skip is #4." centred, with a small
    arrow cue pointing right.
  - Slides 3–7 (one tool each): ranking badge top-left, tool name, "best for" line,
    one-line benefit, one-line limitation, "find it here" cue at the foot.
  - Slide 8 (recap): all five names in one column, one line each, plus the single next
    action: "Try #4 first."
- **Palette balance:** dark ground dominates; cream for headline and body; yellow used
  once per slide only — on the ranking badge on item slides, on the count on the cover.
- **Headline text (verbatim):** "5 tools that save an hour a day"
- **Proof element:** real screenshots of each tool's main screen, cropped to the feature
  being ranked — no mockups, no stock dashboards.
- **Text density check:** cover 8 words; item slides 28–34 words each; smallest text
  30 px (the "find it here" cue).
- **Dimensions:** 1080 x 1350, 8 slides.
- **Alt text:** "Carousel ranking five tools that save an hour a day, with a real
  screenshot and one benefit and one limitation per tool."

**Gate result for this brief (illustrative):** 15/15 PASS — hook readable in under 2
seconds at phone size; all five ranking cards carry badge, name, best-for, benefit,
limitation, and find-it cue; contrast checked (cream on dark ground, yellow badge on
dark ground); no ghost words found on the full-size scan.

### Before / after layout example (same slide, same words)

**The slide:** item #4 of the listicle — the tool's name, its best-for line, its benefit,
its limitation, and the find-it cue.

**BEFORE (fails the gate):**

- Headline, tool name, benefit, limitation, and cue all stacked in one centred column
  on a flat dark field, with a small "TRY IT" button shape at the bottom.
- The tool's real screenshot is absent; a generic laptop stock photo sits behind the
  text at low opacity.
- The limitation is set in 22 px grey text — unreadable at phone size.
- Fails gate points 2 (no visual story, no proof), 3 (no real subject), 7 (text too
  small to scan), and 15 (identical layout to the previous three item slides).

**AFTER (passes the gate):**

- Ranking badge "4" large in the top-left corner, in the accent colour.
- Tool name as the headline, top third, left-aligned; the real screenshot of the tool's
  main screen fills the middle band, with the benefit as a one-line caption beneath it.
- Best-for line and limitation sit side by side at the foot in 34 px cream text — the
  limitation is honest and legible, not hidden.
- The find-it cue is a plain text line, not a button shape; the flat-field-plus-button
  construction is gone.
- The accent balance differs from slides 3, 5, 6, and 7 (badge position and screenshot
  crop change), so the slide is recognisable as its own item, not a copy.
- Passes the gate 15/15: hook, story, information, proof, hierarchy, and brand are all
  present; every word was read against the brief in the full text scan.

## Slide-by-slide layout patterns

Use these as starting patterns, not templates to copy blindly. Every post still gets its
own composition inside the pattern. Two rules from the wider field, adopted here:
every slide must survive alone as a screenshot (a reader who sees one slide out of
context still gets value), and at least one slide must be useful enough to save
(a checklist, framework, or recap — the save slide).

### Pattern A — Listicle / ranking (e.g. "5 tools that do X")

- **Slide 1 (cover):** headline (3–8 words) + the count ("5 tools") + one strong focal
  image. No list on the cover.
- **Slide 2 (second hook):** the payoff — what the reader gets by swiping ("the one most
  people skip is #4"). This slide decides whether the swipe happens. (REPORTED:
  Instagram may re-show a skipped carousel starting at slide 2, so slide 2 is a
  second cover, not a continuation.)
- **Slides 3–7 (one item each):** ranking badge (large, top corner) · name · "best for"
  (one line) · key benefit (one line) · limitation (one line, honest) · where-to-find-it
  cue. Same structure, different accent balance and imagery per slide.
- **Last slide:** recap in one line + the single next action. No new information here.

### Pattern B — Tutorial / how-to (e.g. "Do X in 4 steps")

- **Slide 1 (cover):** outcome headline ("Do X in 4 steps") + the finished result shown,
  not described.
- **Slide 2 (second hook):** the hardest part named honestly ("step 2 is where most
  people stall") + what makes it doable.
- **Slides 3–6 (one step each):** step number (large) · action in one line · the real
  screen or result for that step · one common mistake to avoid.
- **Last slide:** the full sequence in miniature (4 steps, one line each) + next action.

### Pattern C — News / alert (e.g. "X just changed — what it means")

- **Slide 1 (cover):** the change in plain words + "NEW" or date marker + one focal image.
  No hype words the content cannot support.
- **Slide 2 (second hook):** who it affects and who it does not — the eligibility line,
  on the slide, not buried later.
- **Slides 3–5:** what changed (real screenshot or quote) · what it means in practice ·
  what to do now (one concrete action).
- **Last slide:** the one-line summary a reader can repeat to someone else.

### Pattern D — Build-along (e.g. "Build X with me")

- **Slide 1 (cover):** the thing being built, shown finished + the time or effort it takes.
- **Slide 2 (second hook):** the starting point — what you need before step 1.
- **Slides 3–8 (one stage each):** stage name · the real screen or artefact at that
  stage · one decision the reader must make at that stage.
- **Last slide:** the finished artefact + what to build next.

## Thumbnail concept-to-layout spec

A thumbnail is briefed in three stages. Never go from a one-line idea straight to a final.
This spec produces a *brief and a layout* — for a finished YouTube thumbnail file,
hand the chosen layout to `youtube-thumbnail-design`.

1. **Brief (one paragraph).** The video/post title, the one feeling the thumbnail should
   create (curiosity, surprise, clarity), the focal image, and the exact cover text
   (verbatim, 1–4 words that ADD to the title instead of repeating it).
2. **Three concepts.** Three distinct layouts from the same brief — different focal image,
   different text position, different accent. Each concept is one sentence: what is in the
   picture, where the text sits, what feeling it creates.
3. **Chosen layout.** Pick one concept. Write the full layout spec: focal image, text
   (verbatim), text position and size, background, accent, safe margins on all four sides.
   Then make it. Check the finished thumbnail at full size AND at stamp size (the size it
   appears in a feed). If the text is unreadable at stamp size, or touches any edge, or
   any word is misspelled, regenerate — never ship it.

### Thumbnail lab workflow (weekly, 30 minutes)

Run once a week, same day each week.

1. Pick the week's most important post and write its thumbnail brief.
2. Generate the three concepts. Compare them side by side at stamp size, next to the
   thumbnails they will appear beside in a feed.
3. Pick the winner by one question: which one gets clicked first, and why? Write the
   answer in one line.
4. Make the one change that would make the winner win by more. Regenerate once if needed.
5. File the brief, the three concepts, and the winner's one-line reason with the post.

## Type scale + spacing tokens

Recommended starting values. They are design tokens, not laws — adjust them to your
fonts, but keep the ratios and the minimum sizes.

| Token | 1080 x 1350 | 1000 x 1500 | 1080 x 1920 |
|---|---|---|---|
| Headline | 110–140 px, bold | 100–130 px, bold | 120–150 px, bold |
| Sub-headline | 56–64 px | 52–60 px | 60–72 px |
| Body | 40–46 px | 38–44 px | 42–48 px |
| Caption / label | 30–34 px | 28–32 px | 32–36 px |
| Smallest text allowed | 28 px | 26 px | 30 px |
| Outer margin (all sides) | 72 px | 64 px | 84 px |
| Gutter between elements | 36 px | 32 px | 40 px |
| Line height (headline) | 1.05x | 1.05x | 1.05x |
| Line height (body) | 1.35x | 1.35x | 1.35x |

Rules for the tokens:

- **Headline 3–8 words.** More words means smaller type; smaller type means a weaker
  hook. Cut words before you cut size.
- **Headline 3 lines maximum.** Measure the block before placing anything under it:
  block height = lines × size × 1.05. The focal band starts below the headline block
  plus one gutter — never at a fixed height. A 4-line headline at the top of the token
  range collides with the image band (found in testing: a 4-line 132 px headline ran
  into the focal band). If it wraps to 4 lines, cut words first; if the words are
  essential, drop to the low end of the token range and re-measure.
- **One headline size per visual.** A second, slightly smaller headline competes with the
  first and both lose.
- **Minimum sizes are floors.** Text below the floor is unreadable at phone size — cut
  the words instead. Body text never goes below 40 px at 1080 px width; the smaller
  sizes in the table are for labels and cues only.
- **Margins are safe zones.** Nothing — text, logo, or badge — crosses the outer margin.

## Ghost-word discipline

**Ghost words** are words an image generator renders that look like text at a glance but
are faint, half-formed, misspelled, or unreadable on close inspection — letter-like shapes
in a background, a blurred label, a sign that says nothing. They are a defect, not a
detail, because a viewer reads them as sloppy or deceptive even when they cannot make out
the letters.

- Scan every generated image at full size specifically for ghost words before the
  general text scan. Zoom into backgrounds, signs, screens, and book spines.
- Any ghost word = regenerate or rebuild. Never crop around it and hope nobody notices.
- If a generator keeps producing ghost words in the same spot, change the brief: remove
  the background element that carries the fake text, or replace it with a plain field.
- Real text that is intentionally small (a genuine UI label) is not a ghost word — but it
  must still be spelled correctly and readable at phone size, or it is cut.

## Canonical-facts lock

A **canonical-facts lock** is a single file you maintain listing every fact and figure
your visuals are allowed to state: product names, prices, dates, counts, rankings, and
quotes — each with its source. It is the only source of truth for numbers on visuals.

- Every number, price, date, and quoted claim on a visual must match the lock exactly.
  If the lock says "37", the visual says "37" — never "40" or "37+".
- A figure whose qualifier matters ("over", "more than", "estimated") carries the
  qualifier ON the visual, next to the figure, at headline size — never only in the
  caption or the voiceover.
- If a fact is not in the lock, it does not go on a visual. Either verify it and add it
  to the lock first, or cut it.
- When a fact changes, update the lock first, then rebuild every visual that states it.
  Never patch the visual and leave the lock stale.

## Weekly creative-research routine (30–45 minutes)

Run once a week. The point is principles, not copying.

1. **Sample (10 minutes).** Collect 10 high-performing visuals in your niche from the
   past week — feeds, search results, or a platform's trending surface. Save them with
   their source and date. Do not download or reuse anyone's image; you are studying
   layout, not taking assets.
2. **Record (10 minutes).** For each one, write one line: what the hook is, where the
   text sits, what the focal image is, and what makes it stop the scroll.
3. **Extract principles (10 minutes).** Look across the 10. Write 3–5 principles in your
   own words (e.g. "the winning covers put the result, not the tool, in the top half").
   A principle is a rule you can apply to a different topic — never a layout to copy.
4. **Test one variable (next post).** Pick one principle and apply it to one visual in
   the coming week. Change one variable only, so you can tell whether it helped. Note
   the result next to the principle.

## Troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| Visual looks like every other post | Same layout + same accent balance repeated | Change the layout pattern and the accent balance, not just the headline |
| Text unreadable at phone size | Below the minimum token, or colour-only contrast | Raise the size to the token floor; check WCAG contrast; use a brightness difference, not just hue |
| Generator keeps misspelling a word | The word is long or the brief buries it | Shorten the headline to 3–8 words; put the exact text in quotes in the brief; regenerate |
| Ghost words in backgrounds | Generator filling empty zones with fake text | Remove the background element from the brief; replace with a plain field |
| Thumbnail loses at stamp size | Text too small or focal image too busy | One focal image, 1–4 words, high contrast; test at stamp size before shipping |
| Headline collides with the image band | Headline wrapped to 4 lines at a fixed band height | Measure the headline block (lines × size × 1.05); start the band below it plus one gutter; cut words first |
| Numbers on the visual are challenged | Visual disagrees with the facts lock | Fix the lock first if the lock is wrong; rebuild the visual from the lock |
| Cover cropped on the profile grid | Key content near the left/right edges | Keep cover words and focal image inside the centre; the grid crops ~34 px per side |

## Known limits

- This skill designs and checks visuals; it does not generate them and it does not
  guarantee performance. A visual that passes the gate can still underperform — the
  weekly research routine is how you learn what your audience actually responds to.
- Contrast ratios are for text legibility. They do not make a bad layout good.
- Dimensions and platform behaviour change. Re-check the size table against the
  platform's current specs before a format you have not shipped in a while.
- The example palette and type scale are starting points. If your brand system differs,
  substitute it and keep the gate — the gate is the skill, the palette is an example.
- Type tokens are practitioner starting values, not platform rules. One current guide
  (Heijdenrijk, Oct 2026) puts body text higher, around 54 px at 1080 px wide, and
  cover headlines at 130–150 px in a heavy sans. If your audience reads on small
  phones, test the larger sizes — the floors in the table are minimums, not targets.
