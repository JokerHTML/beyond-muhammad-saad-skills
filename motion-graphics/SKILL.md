---
name: motion-graphics
description: Make text and graphics move with purpose in any reel — five locked easing tokens, phase-list hero builds, and timing budgets that keep every animation explaining, emphasizing, or guiding the eye.
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
sources:
  - awesomeskills.dev, "motion-animate" (four laws, timing table, overshoot caps, ms-first authoring)
  - claudepluginhub, "motion-design" (Material Design 3 bezier standards, motion personality)
  - Robert Penner easing equations (easeOutBack constant 1.70158 ≈ 10% overshoot)
  - Disney's 12 principles (slow in / slow out) via The Illusion of Life
  - In-house playbook: 24-move camera mapping (Part F table + 100-command list) — inlined in §CAMERA, no external file needed
---

# Motion Graphics System

## PURPOSE
Animate text and graphics in reels so every movement EXPLAINS, EMPHASIZES,
or GUIDES attention — motion serves the story or it is removed. All frame
numbers in this skill are at **30 fps** unless stated; 1 frame = 33.3 ms.
See §FPS for the 24/60 fps conversion — author durations in milliseconds,
convert to frames per delivery fps, never hardcode 30 fps counts.

## WHEN TO USE
Every animated reel. This skill owns HOW elements move; the pipeline
around it (render, assembly, grade, publish) is owned by the reel skill
that calls it.

## THE EASING TOKENS (only these — never invent a curve per scene)
Precompute each as a 101-point lookup table at script start. Reuse across
the whole series: series consistency = token consistency.

| Token | cubic-bezier | Use | Duration |
|---|---|---|---|
| `enter` | (0.16, 1, 0.3, 1) easeOutExpo | text/graphic entrances | 9–15f (300–500ms) |
| `hero_enter` | (0.05, 0.7, 0.1, 1) Material emphasized-decelerate | the one hero element per scene | 11–15f |
| `move` | (0.65, 0, 0.35, 1) | on-screen moves | 9–12f |
| `exit` | (0.7, 0, 0.84, 0) ease-in | exits — always 30–50% SHORTER than the entrance | 6–9f |
| `pop` | easeOutBack, s=1.70158 (~10% overshoot) | badges, keywords, numbers, prices ONLY | 9–14f |

- `ease_out_back(t, s)`: `u=t-1; return 1 + (s+1)*u**3 + s*u**2`. Hero word
  only: s=2.2 (~15%). Clamp the final frame exactly to target (no 1px jitter).
- Overshoot caps [awesomeskills motion-animate]: small UI/icon elements
  cap at 1.06 — anything past 1.1 on a small element reads as a cheap
  bounce. The 1.10 `pop` is for badges/keywords/numbers only, never for
  panels or small UI.
- NEVER overshoot a large panel/card — wobble on a big surface reads sloppy.
- NEVER animate scale from 0% — scale-land is 95%→100% + fade.
- Duration-based easing only. No per-frame physics integration (springs
  drift and break VO sync); bake any spring feel into the lookup table.
- Four laws [awesomeskills]: nothing is linear; nothing enters at once
  (60–120 ms between entrances); the camera is never fully still; nothing
  is metronomic (vary durations and cut spacing).

## THE BUILD SYSTEM (every hero element, in order)
1. **Anticipation:** 2–4f counter-move, 5–8% opposite direction (dip 8–12px or scale 0.95).
2. **Main action:** 8–12f on `enter`/`hero_enter`.
3. **Overshoot:** pass the rest point by 6–10px (or scale 1.03–1.08), 2–3f — via `pop` or the phase list.
4. **Settle:** 3–6f decaying to exact rest.
5. **Hold:** ≥12–18f still before the next idea. Total hero build ≈18–24f
   (build phases only — hold is additional, per §TIMING BUDGETS).
Implement as a phase list per element:
`[(3, 0, -10, enter), (10, -10, +8, enter), (5, +8, 0, enter)]`,
sampled per global frame. A single Back curve cannot anticipate — use
phases when anticipation matters. Reference values (verified by test):
anticipation ends at exactly −10 (f3), overshoot peaks at exactly +8
(f13), settle ends at exactly 0 (f18), hold is still (f25).

## LAYER DISCIPLINE
- **Primary/Hero:** full amplitude, smoothest ease, lands first.
- **Secondary/Support:** 30–50% amplitude, lag **+2–3f** behind primary
  (follow-through), 60–70% of primary duration. Every layer has its OWN
  `delay_frames` + `duration_frames` — never one global `t`.
- **Ambient:** slow sine drift only (`offset = 3*sin(f*0.03 + phase)` px),
  <10% change, loops.
- **Simultaneity cap:** with 3+ elements, ≤⅓ in active motion on any
  frame; delay lowest-rank elements 2f to enforce.
- **Distance cap:** no element travels >⅓ of screen without an
  intermediate keyframe/scale/opacity change (long unbroken slides =
  template motion).

## STAGGER (lists, bullets, checklist builds)
- Offset **2f per item** (3f for slow/premium builds, 1f for dense grids).
- Per item: fade + translateY 12–20px + `enter`. Line builds overlap: next
  line starts when the previous is ~70% done.
- **Whole-group reveal capped at 18–24f.** If count × stagger > cap,
  shrink the stagger — never extend the total.

## REVEALS (prefer clipping over fading)
- **Baseline mask rise** (the premium editorial look): text rises from
  behind its line mask, 10–14f on `enter`, 0 rotation. PIL: per-frame
  `crop()` IS the matte — `clip_h = int(line_h * ease(t))`, paste the
  slice into a fixed clip box.
- **Mask wipe L→R:** 12–18f ease-in-out, feather the matte edge 2–4px
  (hard edge = cheap).
- **Squash & stretch:** landing squash scaleY 0.92–0.95 / scaleX 1.05–1.08
  (`sx*sy ≈ 1`), recover 4–6f on `pop`; fast travel stretches 1.05–1.12
  along motion direction at peak velocity; numbers squash ONCE on the
  final value landing.
- **Arcs:** add a perpendicular sine bulge of 5–10% of travel distance at
  the path midpoint (`y += amp*sin(pi*t)`). Straight-line organic motion
  reads mechanical.

## TRANSITIONS (grammar of six — hard cut is the default)
1. **Hard cut — 0f.** The default. Fast action, beat re-timing, viewpoint change.
2. **Cut on action:** cut at peak velocity; motion continues across the
   cut. Match motion DIRECTION across every cut so the eye never resets.
3. **Match cut:** hero shape at identical `(cx, cy, bbox_w)` on both
   sides; slow→fast→slow, cut at the fastest point. Just cut — no
   transition frames.
4. **Dissolve — 12–24f, RARE:** time passing / location change only.
5. **Infinite zoom:** scale 1.0→3.0+ over 20–30f through a sub-frame
   (window/screen/logo shape); never stop zooming between scenes. PIL:
   shrink the centre crop box per frame, resize back to full canvas.
6. **Morph — 15–24f:** same-fill shapes only, logo/icon transformations;
   interpolate polygon vertices (same vertex count); text→shape ≈ 8f
   cross-dissolve while scaling.
Whip pan: 6–10f blur + horizontal stretch, direction matched both sides,
3f either side of the cut.
**Cut test (mandatory):** if a transition cannot answer "what does this
shot give me the last one didn't?" — hard cut on the beat/motion peak instead.

## CAMERA LANGUAGE (inlined — no external playbook file needed)
Every storyboard names ONE camera move per beat from the table below —
never "zoom in a bit." A move must earn its place via PURPOSE (EXPLAIN /
EMPHASIZE / TRANSITION / RESET / EMOTE / PROVE / CLARIFY). One beat = one
move = one idea; moves land ON the beat, starting ~0.05 s early.

| Beat role | Move | Easing token | 2D implementation |
|---|---|---|---|
| HOOK (0–1s) | `/impact zoom` or `/fast push` | `pop` | scale ramp |
| LOCK-IN | `/slow push` | `move` | scale 1.00→1.06 |
| New idea / transition | `/whip pan` (+ directional blur) | `exit`→`enter` | translate + blur |
| Vertical energy shift | `/whip tilt` | `exit`→`enter` | translate + blur |
| Reveal the payoff | `/dolly out` / `/cinematic pullback` | `move` | scale 1.06→1.00 |
| Emphasize a word/stat | `/dolly in` / `/push in` | `hero_enter` | scale + hold |
| Shift between 2 ideas | `/rack focus` (blur ramp A→B) | `move` | blur ramp layers |
| Depth / premium feel | `/parallax move` (2–3 layers, different speeds) | `move` | multi-layer |
| Scene drift / life | `/micro shake` (seeded, deterministic) | — | ±2px noise |
| Lateral comparison | `/truck left` / `/truck right` | `move` | translate |
| Before → after | `/pan left` / `/pan right` | `move` | translate |
| Vertical list scroll | `/pedestal up` / `/pedestal down` | `move` | vertical translate |
| Grand reveal | `/crane reveal` (simulate: scale + rise) | `hero_enter` | scale + translate |
| CTA resolve | `/pull back` → settle | `exit` | scale down, hold |
| Speed contrast | `/speed ramp` (slow→fast on the beat) | — | frame remap |
| Settle / breathe | `/smooth glide` or `/floating camera` | `move` | slow drift |
| Stylized beat | `/dutch angle` (≤8°, brief) | `pop` | rotate |
| Loop energy | `/accelerate` into loop point | `enter` | ease ramp |

**Provenance note:** the source playbook labels this list "the 24
essential moves" but lists 18 rows — those 18 are inlined verbatim above.
The remaining 6 rows below complete the 24 from the same author's
100-command list (same beat-role logic, not from the playbook table):

| Beat role | Move | Easing token | 2D implementation |
|---|---|---|---|
| Slow-down beat | `/slow motion` | `move` | frame remap (hold frames) |
| Energy burst | `/motion burst` | `pop` | scale + translate burst |
| Subject follow | `/tracking shot` / `/follow cam` | `move` | translate, subject framed |
| Focus snap | `/focus snap` | `move` | fast blur ramp A→B |
| Wide establish | `/establishing shot` | `move` | scale down + rise |
| Dramatic low | `/low angle` (brief) | `hero_enter` | scale + vertical shift |

BANNED as decoration: `/camera shake`, `/dramatic shake`, `/360 spin`
as filler, `/epic shot` without a payoff, any orbit needing true 3D in a
2D pipeline. True-3D moves (`/orbit 360`, `/drone fly`, crane arcs) are
reserved for AI-video-generated segments — never faked badly in 2D.
Camera gotchas: whip moves NEED motion blur or they read as glitches
(directional blur along the travel axis); rack-focus blur ramps must be
symmetric in duration (out = in) or the cut feels cheap.

## FPS ADAPTATION (24 / 60 fps)
Author every duration in **milliseconds** and convert to frames at the
delivery fps (`frames = round(ms × fps / 1000)`). Frame counts in this
skill are 30 fps values — do not copy them into a 24 or 60 fps build.

| Duration | 24 fps | 30 fps | 60 fps |
|---|---|---|---|
| Hero build 600 ms | 14f | 18f | 36f |
| Entrance 300–500 ms | 7–12f | 9–15f | 18–30f |
| Exit 200–300 ms | 5–7f | 6–9f | 12–18f |
| Stagger 67 ms (2f @30) | 2f | 2f | 4f |
| Hold floor 400–600 ms | 10–14f | 12–18f | 24–36f |

At 60 fps, double the frame counts — do not halve the durations. At
24 fps, prefer the millisecond values over rounded frame counts when a
1-frame rounding error would break a beat landing.

## TIMING BUDGETS (per scene, non-negotiable)
- Scene frame budget = `build (12–18f) + HOLD (≥ word_count × 15f) +
  exit (6–9f)` at 30 fps. Frames running short? Steal from build/exit —
  **NEVER from hold**.
- Reading floor: an information-bearing word gets ≥9f on screen;
  on-screen informational text runs at **60–90 wpm** even when the VO
  runs 150 wpm — show phrases, not every spoken word.
- **Reconciling the two numbers (fixed 23 Nov 2026 — they conflicted as
  written):** `word_count × 15f` at 30 fps is 0.5 s/word = 120 wpm,
  which is FASTER than the 60–90 wpm reading floor (20–30f/word).
  The two rates apply to different cases, and the checker must know
  which one governs the scene:
  - **VO-matched text (the 15f/word budget):** the voiceover speaks the
    same words the viewer sees — the viewer skims, not reads. The
    15f/word floor holds.
  - **Standalone text (the 60–90 wpm floor):** text the viewer must read
    with no matching VO — use **20–30f/word** (20f = 90 wpm, the fastest
    standalone rate). A scene whose on-screen text carries information
    the VO does not speak fails the gate at 15f/word.
  - The ≥9f per-word figure is a VISIBILITY floor for a single
    emphasized word (a keyword, a number flashing on), not a reading
    rate — never use it to justify a fast scene.
- Reel's final phrase holds a full beat longer than any other hold.

## QUALITY RULES
- One focal element animates first; entrance order = reading order.
- Animate hook + emphasis words only. If every word does a backflip,
  nothing stands out.
- Exits leave in the direction motion was heading; never reversed; never
  the entrance ease played backwards.
- Text timing comes from the VO cue sheet
  (`(start_f, end_f, text, emphasis)`) — never hardcoded inside draw code.
- Motion that draws attention to itself instead of the idea = defect.
  REJECT → simplify → re-render.

## FAILURE MODES
- Everything stopping on the same frame → add follow-through lags (+2–3f per layer).
- Group reveal overrunning → shrink stagger, cap 24f.
- Wobble on panels → `pop` was applied to a large surface; switch to `enter` at 95%→100%.
- Motion feels "template" → check distance cap, simultaneity cap, and whether easing tokens were replaced with ad-hoc curves.

## VERIFICATION
- Spot-check rendered frames at: anticipation frame, peak-overshoot
  frame, settle frame, mid-stagger frame — values must match the phase
  list exactly.
- Count simultaneously-moving elements on 5 random frames: ≤⅓.
- Every scene's hold ≥ word_count × 15f for VO-matched text, or
  ≥ word_count × 20f for standalone text — verify from the cue sheet,
  not by eye (see the §TIMING BUDGETS reconciliation).

## STOP CONDITIONS
- Stop if a scene needs a 7th transition type or a new easing curve to
  work — the scene concept is wrong, not the toolbox. Rebuild the scene.
