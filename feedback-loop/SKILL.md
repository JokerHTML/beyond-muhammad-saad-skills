---
name: feedback-loop
description: Turn every customer question, comment, objection, or refund signal into a classified, routed, fixed, and verified improvement — one class, one action, one log entry per item.
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
---

# Feedback Loop

## Purpose

Turn every customer question, comment, objection, or refund signal into a classified, routed, fixed, and verified improvement — without letting every request become a product feature.

## When to Use

Any customer question, comment, objection, refund request, support email, or review — about the product or the content. Applies to any product and all published content.

## Inputs

- The **verbatim** feedback (exact customer words, not a paraphrase)
- Source: email / comment / review / refund request / DM
- Date received

## The 9 Classes

Each item gets **exactly one** class. If two seem to fit, pick the one that decides the action; record the other candidate as part of the root cause, never as a second class.

| Class | Distinguishing definition | Example |
|---|---|---|
| QUESTION | Asks for information; nothing is broken or wrong. | "Does this include templates?" |
| CONFUSION | The customer is stuck or misreads something that works as designed. | "I can't find where the checklist lives." |
| OBJECTION | Pushes back on price, value, or fit before/after buying. | "It's too expensive for a PDF." |
| BUG | The product behaves differently from its documented or intended behaviour. | "The download link gives a 404." |
| MISSING CONTENT | Something the product reasonably should contain is absent. | "There's no chapter on follow-ups." |
| EXPECTATION GAP | The customer expected something the product never promised — or the sales page promised something the product doesn't do. | "I expected live coaching calls." |
| FEATURE REQUEST | Asks for new behaviour or capability. | "Add a Notion version, please." |
| POSITIVE SIGNAL | Praise or a result worth learning from (and, with permission, quoting). | "Got my first client in a week with this." |
| REFUND SIGNAL | The customer asks for, or clearly moves toward, a refund. | "I want my money back." |

The three that blur — **QUESTION vs CONFUSION vs EXPECTATION GAP**: a QUESTION wants a fact and is answered, not fixed; CONFUSION means the thing works but the customer can't use it (fix the guidance/onboarding); EXPECTATION GAP means the customer's mental model of the product is wrong (fix the promise in the listing/content, or the product if the promise was right).

## Process (7 steps)

1. **Capture** the verbatim feedback + source + date. Do not paraphrase away the customer's phrasing.
2. **Classify** into exactly one of the 9 classes above.
3. **Identify root cause.** Ask: is this the product, the listing copy, the onboarding, a missing file, or a wrong expectation set by our content? **Check the listing / sales page BEFORE blaming the product.** Also attach customer context to the record: what they bought, which version, and what they were trying to do.
4. **Decide action** — exactly one: PRODUCT FIX / FAQ FIX / CONTENT IDEA / SALES PAGE FIX / ONBOARDING FIX / NO ACTION. Name one accountable owner for the item.
5. **Fix at the smallest effective level.** One fix per feedback item. Do not bundle unrelated changes.
6. **Verify the fix** by re-testing the exact customer scenario end to end. For listing fixes, re-read the listing end to end and re-run your product QA checklist. Unresolved items stay OPEN in the log — never mark resolved on intent.
7. **Log it + close the loop.** Every item gets a log entry, including NO ACTION items with the reason. Then tell the customer what changed (or what happens next) — a loop is closed only when the customer hears the outcome.

## Worked Example

**Item:** email, 2026-11-23. Verbatim: *"The download link in my email gives a 404 when I click it."*

1. **Capture:** verbatim + source (email) + date recorded.
2. **Classify:** BUG — the product behaves differently from its documented behaviour (the link should deliver the file).
3. **Root cause:** checked the sales page first — it promises instant download. Reproduced against the actual package: the emailed link points to a retired file version. Root cause = product/delivery file, not the listing. Owner: [product owner].
4. **Action:** PRODUCT FIX.
5. **Fix:** re-pointed the email download link to the current file version. One fix only.
6. **Verify:** clicked the emailed link from a fresh test inbox — file downloaded and opened without error. PASS.
7. **Log + close the loop:** entry `FB-T01` written (see log format below); customer told the link is fixed and asked to retry.

**Second example (refund):** *"I expected live coaching calls, this is just a PDF — I want my money back."* → class REFUND SIGNAL (the expectation gap is the root cause, not a second class). Root cause: the sales page said "live coaching calls included" while the product is a self-paced PDF guide. Action: SALES PAGE FIX + same-day refund triage. Fix: corrected the sales-page line. Verify: re-read the page end to end; the claim is gone. Log entry `FB-T02`; customer acknowledged the same day and offered the refund path under your stated refund policy.

## Refunds

- Refund signals get **same-day triage** — always.
- Offer the fix first where a fix exists; if the customer still wants a refund, follow **your stated refund policy** ([your refund policy — terms, window, and process; write them here before using this skill]).
- **No refund terms are assumed by this skill.** The source of this skill referenced "30-day fix-first refund terms" without defining them; that reference was cut rather than invented. Do not quote refund terms you have not written down.
- Escalate refund disputes (anything beyond a straightforward fix-first refund) — do not resolve them unilaterally.

## Quality Rules

- Do not turn every customer request into a product feature. Most requests are information gaps, not product gaps.
- Expectation gaps are usually fixed in the listing/content, not the product. Fix the promise, not just the thing.
- Positive signals feed testimonials **ONLY with explicit customer permission**. Never fabricate testimonials, reviews, or screenshots.
- Honesty rules apply: never promise what the product doesn't contain. Product claims stay within your product's own source of truth.
- Route by threshold, not everything: a single FEATURE REQUEST is logged and counted; it becomes a roadmap item only when the same request recurs from multiple customers. Routing every item to the team trains people to ignore the channel.

## Failure Modes

- **Misclassification.** If new info changes the picture, re-classify. The first label is a hypothesis, not a verdict.
- **Fixing the product when the listing set the wrong expectation.** Always check the listing and the content that drove the purchase first.
- **Silent fixes with no log.** Every fix gets logged. An unlogged fix is a future regression nobody can trace.
- **Replying without closing.** An acknowledgement is not a closed loop. The item closes when the customer is told the outcome.

## Output — Log Entry

One entry per item, in `[your log file]` (internal, never customer-facing). Fields:

| Field | Content |
|---|---|
| ID | Sequential, e.g. FB-001 |
| DATE | Date received |
| SOURCE | email / comment / review / refund request / DM |
| VERBATIM (short) | Customer's exact words, trimmed |
| CLASS | Exactly one of the 9 |
| ROOT CAUSE | Product / listing / onboarding / missing file / wrong expectation |
| ACTION | Exactly one of the 6 |
| OWNER | Named person |
| STATUS | OPEN / CLOSED |
| VERIFIED | YES + how, or NO |
| CUSTOMER NOTIFIED | YES + date/channel, or NO |

## Stop Conditions

Stop and escalate to the account owner on:

- Refund disputes (anything beyond a straightforward fix-first refund)
- Legal or compliance concerns (FTC-adjacent claims, tax, IP disputes)
- Any feedback suggesting the product is fundamentally misrepresented

Do not attempt to resolve these three categories unilaterally.
