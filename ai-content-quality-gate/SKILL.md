---
name: ai-content-quality-gate
description: Stop bad AI-assisted posts before they publish — a fail-closed 92/100 quality gate with 8 automatic critical failures and bundled builder + visual checklists for any creator.
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
---

# AI Content QA

## Purpose

Fail closed. No post ships unless it passes the 92/100 quality gate **and** every critical gate. Revise, re-check, or reject — never lower the bar to meet a calendar. This skill is self-contained: the builder checklist and the visual checklist it depends on are bundled below, not pointed at elsewhere.

## When to use

- Final check on every AI-assisted post, after drafting and before approval.
- Any time a claim, link, price, prompt, or visual is added or changed after the first pass.

## Verdicts

Every run ends in exactly one verdict:

- **Publish** — passes the score bar and every critical gate. At most three optional nits may be listed; style preferences are not defects.
- **Fix first** — fails the score bar or a fixable critical gate. Each problem is located and given a concrete fix. Re-run the gate after fixing.
- **Hold** — fails an unfixable critical gate (e.g. a rights problem, a fabricated test, a claim no source supports). Do not publish; escalate or reject.

Pressure never changes the verdict. A deadline is not evidence.

## Rules (hard)

- **92/100 minimum AND every critical gate passed.** A post scoring <92 or failing any critical gate is revised until it passes or marked REJECTED with the reason — never shipped as passing.
- **Independent verification:** the checker re-opens sources and links itself; it does not trust the drafter's notes.
- **One FAIL on the builder checklist or the visual checklist = revise, never ship.**
- **Never verify from memory.** A statistic, price, or feature that "sounds right" is unverified until a source is opened.
- **Never fill a gap with an invention.** No made-up URLs, statistics, alt text for an image you cannot see, or replacement testimonials. Name what is needed and who has it.
- **Never represent a draft as tested, a recommendation as installed, or a scheduled post as published.**
- **Verification depth scales with stakes.** A low-stakes internal draft gets a claims-only check; anything published, anything a reader will act on, and anything with prices, rights, or policy claims gets the full gate. When in doubt, run the full gate.
- **Count, don't eyeball.** Character counts, hashtag counts, em-dash counts, and hook windows are measured with a tool, not estimated.

## Scored gates (100 points total)

| Gate | Points |
|---|---|
| Accuracy / evidence | 20 |
| Practical usefulness | 15 |
| Prompt / workflow completeness | 15 |
| Tool research / links | 10 |
| Hook / storytelling | 10 |
| Originality | 10 |
| Visual / audio | 10 |
| Platform-native structure | 5 |
| SEO / accessibility | 5 |

Score each gate, total them, and record per-gate points in the QA record. Deduct for: unverified wording, thin usefulness, incomplete prompt block, untested claims presented as tested, weak hook, derivative structure, visual defects, identical copy across platforms, missing SEO output or alt text.

## Automatic critical failures (any one = Fix first or Hold, regardless of score)

1. Unverified factual claim, fabricated tool feature, fake ranking, fake test, or misleading "best" claim.
2. Broken, unsafe, unofficial, or wrong-destination tool link; unverified price or free-tier promise.
3. Missing exact prompt/steps when the content promises to teach a workflow.
4. Copied creator work, reused clips without meaningful original contribution, or unclear rights.
5. Misleading income/viral/monetisation guarantee or inaccurate platform-policy claim.
6. Missing required AI disclosure or other platform disclosure where applicable.
7. Unreadable mobile text, deceptive thumbnail, fake product UI, or major production defect.
8. Identical mass-produced copy across platforms with no native adaptation.

## Builder checklist (bundled — run in order)

- [ ] Claim ledger present; every claim has source URL + date + confidence; no UNVERIFIED figure stated as fact.
- [ ] Every tool link opened (or re-checked) and lands on the official destination.
- [ ] Prompt block complete (8 parts — see the prompt-writing skill) wherever a workflow is taught.
- [ ] Hands-on vs desk-researched label present and true.
- [ ] "Last checked" date present.
- [ ] Hook passes the 4 S's (Subject / Stakes / Speed / Clarity); per-platform hook windows tool-counted.
- [ ] Hook numbers verified — any figure in the hook or first line has a ledger row, like any other claim. (The hook is where unverified stats hide: a stat in the hook is still a claim.)
- [ ] One CTA per platform version; no triple-ask closer.
- [ ] Specificity floor: ≥1 number + ≥1 named entity + ≥1 concrete detail per 100 words.
- [ ] No AI-tell phrases; em-dash ≤1 per 100 words; no emoji walls.
- [ ] Character limits respected (see platform limits table below).
- [ ] Hashtags: IG ≤5, LinkedIn 0–1, others 1–3 where they help. Never stuffed.
- [ ] X native thread (first post no link, ends with a continuation cue; link in the reply). Threads link in first reply only + native topic tag.
- [ ] Visual checklist (below) passed; `VISUAL-GATE:` line written; full text scan done.
- [ ] AI disclosure checked; no income/viral guarantee; no fake GEO/AEO claim.
- [ ] 92/100 score recorded with per-gate points.

## Visual checklist (bundled — 15 points)

- [ ] Every word on the image read against the brief/copy, one by one — no typo, wrong word, duplicated word, or cut-off text.
- [ ] Text readable at mobile size; no text smaller than the platform's readable floor.
- [ ] No deceptive thumbnail: the image promises exactly what the content delivers.
- [ ] No fake product UI: screenshots and interface mockups are real or clearly labelled as mockups.
- [ ] Correct dimensions and aspect ratio for the platform (no stretched, squashed, or wrongly cropped asset).
- [ ] No cut-off elements at the edges or inside platform safe zones.
- [ ] Faces, logos, and key subjects fully in frame.
- [ ] Colour and contrast hold up on a phone screen in daylight.
- [ ] Alt text written for every meaningful image; decorative images marked as such.
- [ ] File format and size within the platform's upload limits.
- [ ] Captions/subtitles accurate and synchronised (video).
- [ ] No watermark, stock-preview mark, or third-party branding that was not cleared.
- [ ] No personal data, passwords, or private information visible in any frame.
- [ ] Audio (if any) is clear, correctly levelled, and rights-cleared.
- [ ] Visual matches the hook and the first line of copy — one story, not two.

## Platform limits (verified 23 Nov 2026 — re-check before relying on any figure)

| Platform | Hard text limit | Notes |
|---|---|---|
| X (free) | 280 chars per post | URLs count as 23, emoji as 2. Paid tiers allow longer posts; write to 280 unless the audience is known to be paid-tier. |
| Threads | 500 chars per post | One native topic tag per post. |
| Instagram | 2,200 chars caption | Feed folds at ~125 chars — the hook must land above the fold. Max 30 hashtags by platform; this skill caps at 5. |
| Facebook | 63,206 chars | The platform limit is effectively unreachable. House rule: keep feed copy ≤1,024 chars for readability — that is a house rule, not a platform limit. |
| Pinterest | 800 chars (Help page) — write ≤500 always | Pinterest's Help page ("Review Pin specs") says "enter up to 800 characters", and the pin builder hard-blocks above 800 (verified live Oct 2026). Independent checks of the API v5 schema report a 500-char cap for organic/API pins, so ≤500 is the only value safe under both figures. Title 100 chars, keyword in the first 40. |
| LinkedIn | 3,000 chars per post | ~200 chars visible before the fold. 0–1 hashtags. |
| YouTube description | 5,000 chars | First 1–2 lines are the search snippet. |

## Rights / safety checks

- Copyright, commercial-use terms, voice/likeness rights, stock licences, and AI-asset restrictions checked before recommending production or monetisation workflows.
- No passwords, private client info, or confidential data in prompts, visuals, or docs.
- Sources: primary first; independent sources for comparison and context.

## QA record (paste into the post's plan file)

```markdown
## QA-GATE — [post title] — [date]
Verdict: Publish / Fix first / Hold
Score: __/100 — Accuracy __/20 · Usefulness __/15 · Prompt __/15 · Links __/10
  Hook __/10 · Originality __/10 · Visual __/10 · Native __/5 · SEO __/5
Critical failures: none / [list]
Builder checklist: __/16 passed · Visual checklist: __/15 passed
VISUAL-GATE: pass / fail — [note]
Last checked: [date] · Checker: [name/agent]
Fixes required: [list, or "none"]
```

## Why 92/100 here, when the blog-writing skill uses 85/100

Both bars are house rules, not measured or published standards — neither is a scientific threshold. Both are right, because the formats and the stakes differ:

- **Social posts (92/100):** short, single-screen, judged at a glance, distributed to a feed the author does not control, and on several platforms effectively uneditable once published. A weak social post costs reach and trust in seconds, and there is no room inside the format to recover points with depth. The bar is high because the format gives the reader no second chance.
- **Long-form blog posts (85/100):** the format has room to earn points across depth, completeness, and structure, and a published post can be corrected and refreshed after publication. The gate that matters most for blogs is the pass/fail critical-flaw gate, which outranks the score in both skills.

The rule that never changes: a critical-gate failure blocks publication at any score, in either format.
