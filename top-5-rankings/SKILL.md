---
name: top-5-rankings
description: Rank the top 5 tools in any category and prove the order — fixed weighted criteria totalling 100%, verified evidence per tool, a published score table, and honest hands-on vs desk-researched labels. No invented #1.
version: 1.1.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
---

# Top 5 Rankings

## Purpose

Produce Top 5 rankings that earn their order: explicit criteria, verified evidence per tool, a stated method, and an honest hands-on vs desk-researched label. The score table is published so the reader can see why each tool sits where it does.

## When to use

- Any ranked/comparison post.
- Any "best X for Y" claim anywhere.

## Rules (hard)

- **Criteria before picks.** Define what matters in the category before deciding which products should win. Never pick the winners first and fit criteria around them.
- **Never create a Top 5 by copying another creator, repeating affiliate rankings, or picking familiar brand names without checking them.**
- **Never fabricate a test.** If no test was run, the post is desk-researched and says so on the asset.
- **If five credible products cannot be verified, publish a smaller shortlist** ("3 tools worth testing") or retitle to "5 options to compare" — never invent a ranking or an entry.
- **Sponsorship/affiliates never determine ranking.** Disclose any relationship.
- **Add a "last checked" date** to every ranking.
- **Compare on the same task and, where practical, the same prompt/input.** Save test notes and example outputs when a test is run.
- **A tool that fails a must-have is shown but not ranked.** If the category has a deal-breaker (e.g. "must have a free tier"), a tool without it appears in the table with its scores and is marked "not ranked — fails must-have", not forced into a position.
- **Ties share a rank.** Tools within 2 points of each other are effectively tied: declare the tie and choose by reader need, not by a coin-flip decimal.

## Weighted ranking criteria (fixed weights)

| Criterion | Weight |
|---|---|
| Task performance (does it do the stated task well) | 30% |
| Ease of use (learning curve, setup friction) | 15% |
| Value / pricing (free tier generosity, paid step-up) | 15% |
| Features / workflow fit (integrations, fit to the task) | 15% |
| Reliability (uptime, consistency, support) | 10% |
| Privacy / rights / trust (data handling, commercial-use terms) | 10% |
| Availability / support (regions, plans, docs, help) | 5% |

Score each tool 0–10 per criterion, multiply by weight, total /100. Publish the score table (or a readable summary of it) so the reader can see why each tool sits where it does. Where evidence is thin (desk research only), cap the task-performance score and say so — a desk-researched ranking cannot award full marks for performance it never measured. Desk-research cap: task performance ≤7/10.

**How evidence is weighed (strongest first):** the vendor's own specifications, manuals, and pricing pages · independent reviews with direct testing and a clear method · owner-feedback patterns that appear across more than one credible channel · single-source enthusiasm or marketing claims (treated carefully, never the sole basis for a score). Live prices, coupons, badges, and star averages are volatile commerce signals — always carry a "last checked" date.

**Scores are a structured argument, not a magic number.** Every score needs a one-line rationale tied to evidence. A score with no rationale is a guess.

## Required research per tool

- Official product name + verified official URL (domain checked, no lookalikes).
- Best-fit task and intended user — what it is best at, not that it is universally best.
- Current free tier, trial, pricing, credit limits, regional availability — currency + date checked.
- Key features + relevant integrations (no filler features).
- Limitations, output quality, learning curve, privacy/data handling, usage restrictions, known gaps.
- Hands-on tested vs desk-researched — labelled.
- Why it earned its position + which audience member should choose it.

## Hands-on test protocol (use when a test IS run)

1. **Fix one task and one input** (same prompt, same source material) for every tool.
2. **Run each tool once, same day**, save the raw output (screenshot/file) with timestamps.
3. **Score the outputs blind where possible** against the 7 criteria; note failures, hallucinations, and time taken.
4. **Record test notes**: date, tool version/model, exact prompt, input, output excerpt, score.
5. **Label the post "hands-on tested — [date]"** and link or show the evidence. A test that was not run is never described as one.

## Desk-research protocol

1. Build the claim ledger first (see the ai-tool-fact-check skill).
2. Score from documented evidence only; mark task-performance scores as "desk estimate" and cap them at 7/10.
3. State on the asset: "Desk-researched — last checked [date]. No hands-on test yet."
4. Retitle honestly if the evidence cannot support a strict ranking: "5 options to compare" is acceptable; a fabricated #1–#5 is not.
5. Where two tools land within 2 points, run a pairwise check: head-to-head on the single most important criterion (task performance) and say which wins it and why — or declare the tie.

## Worked example — scored table (desk-researched, 23 Nov 2026)

**Task:** research, draft, and illustrate a short AI tutorial post. **Method:** desk research only — prices verified against vendor pages via the claim ledger (see TEST-LOG.md); features from vendor docs; task-performance scores capped at 7/10 per the desk-research protocol. Scores are editorial judgement from documented evidence, not benchmark results.

| Tool | Task 30% | Ease 15% | Value 15% | Features 15% | Reliability 10% | Privacy 10% | Availability 5% | Total /100 |
|---|---|---|---|---|---|---|---|---|
| Google AI Pro | 7 | 8 | 8 | 8 | 8 | 7 | 9 | **76.5** |
| Claude Pro | 7 | 8 | 8 | 7 | 8 | 8 | 8 | **75.5** |
| ChatGPT Plus | 7 | 8 | 7 | 8 | 8 | 7 | 9 | **75.0** |
| Canva Pro | 5 | 9 | 8 | 7 | 8 | 7 | 8 | **70.0** |
| Perplexity Pro | 6 | 8 | 8 | 6 | 7 | 7 | 8 | **69.0** |

Price evidence (last checked 23 Nov 2026, US list): ChatGPT Plus $20/mo, no annual plan · Claude Pro $20/mo or $17/mo billed annually ($200) · Google AI Pro $19.99/mo or $199.99/yr · Perplexity Pro $20/mo or $200/yr ($17/mo billed annually) · Canva Pro $15/mo or $120/yr.

**Reading the table:** the top three sit within 1.5 points — an effective tie. Pairwise check on task performance: all three are capped desk estimates at 7, so no winner on that criterion. Choose by need: Claude Pro for the strongest drafting, ChatGPT Plus for the broadest all-round toolkit, Google AI Pro for Workspace integration. Canva Pro is the cheapest paid plan of the five ($15/mo monthly, $120/yr) and wins on illustration, but cannot research or draft — it is a complement to the top three, not a substitute. Perplexity Pro wins on research depth but loses on drafting and illustration.

## Carousel card spec

Each card: consistent ranking badge (#1–#5) · tool name · "best for" line · key benefit · limitation · access-link cue. Slide 1 = hook + task + "last checked" date. Final slide = how to choose (which tool for which reader) + one CTA. 7–10 slides, 1080×1350, slide 2 = second hook.

## Template (inline — copy per ranking)

```markdown
## Top 5 — [task] — last checked [date]
Method: hands-on tested [date] / desk-researched [date]
Must-have: [deal-breaker, or "none"]
| Tool | Task 30% | Ease 15% | Value 15% | Features 15% | Reliability 10% | Privacy 10% | Availability 5% | Total |
|---|---|---|---|---|---|---|---|---|
| 1. [tool] | | | | | | | | |
Claim-ledger rows: [link or paste]
Best for: [tool] — [reader]; [tool] — [reader]
```

## Limits

- Scores are judgement structured by evidence, not measurements. Say so on the asset.
- Prices and limits drift monthly. A ranking older than 30 days is stale until re-checked — re-run the ledger, do not just change the date.

## Changelog (publish history)

- **v1.1.0 — 2026-11-23 (Round 2):** Renamed `top5-rankings` → `top-5-rankings` (matches the search phrase "top 5", clearer in the repo list); frontmatter description rewritten as a hook. **CORRECTED the worked example:** Canva Pro is $15/mo or $120/yr, not $18/mo or $144/yr — the Round 1 price was wrong (re-verified 23 Nov 2026 against multiple independent Oct–Nov 2026 pricing reads). Canva's Value score corrected 6 → 8 (it is the cheapest monthly plan of the five, not the most expensive) and its total corrected 67.0 → 70.0, moving it above Perplexity Pro (69.0) into 4th. The other four prices re-verified unchanged (ChatGPT Plus $20/mo, no annual; Claude Pro $20/$200yr; Google AI Pro $19.99/$199.99yr; Perplexity Pro $20/$200yr). See UPGRADE-NOTES.md (Round 2) and TEST-LOG.md (Round 2 test: a second ranking with a must-have set).
- **v1.0.0 — 2026-11-23:** Publishable universal version. Full worked score table with 5 real tools, tie rule, must-have rule, evidence-weight hierarchy, desk-research cap (≤7/10) applied.
