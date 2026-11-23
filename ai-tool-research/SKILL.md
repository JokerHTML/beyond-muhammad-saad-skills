---
name: ai-tool-research
description: Verify every tool claim from a primary source before it enters copy, and keep a claim ledger — source URL, date, confidence, and the exact wording the source supports.
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
---

# AI Tool Research & Verification

## Purpose

Verify every tool claim from a primary source before it enters copy, and keep a claim ledger so any claim can be traced to a URL, a date, and a confidence level. A claim with no source is a draft note, not a publishable fact.

## When to use

- Every Top 5, tutorial, news, agent, or comparison post — before drafting.
- Whenever a price, free-tier limit, feature, or availability claim is about to be written.
- Re-check day: open the official page again on the day of posting; free-tier limits change without notice.

## Rules (hard)

- **Primary sources first:** official product site, changelog, docs, pricing page, platform policy page. Independent sources are context, never the sole basis for a price/limit claim.
- **Never fabricate a test, output, speed result, or personal experience.** Label every assessment "hands-on tested" or "desk-researched" — and until a real test run exists, everything is desk-researched by definition.
- **UNVERIFIED = do not publish the figure.** Use only the ledger's "supported wording" for that row.
- **Never quote a figure from a page that did not render** (e.g. a pricing page that returns "Unsupported client", a price table that loads blank, dollar amounts stripped by the reader). Record the render failure, not a guess.
- **No rumours, leaks, or social-only claims as facts.** No benchmark screenshots as facts without corroboration.
- **Regional availability, currency, and date checked** for every price/free-tier claim. Prices are US list unless stated; some vendors render prices in EUR or local currency.
- **Last-checked date on every asset.** Free-tier claims always carry a "last checked [date]".
- **Training-data recall is not evidence.** A price remembered from training is UNVERIFIED until a live page confirms it.
- **Check claims riskiest first.** Prices, limits, and "free" promises first; feature descriptions second; marketing adjectives last.

## Process

1. **Name the claim precisely** (e.g. "Perplexity Pro is $20/mo billed monthly" — not "Perplexity is cheap").
2. **Write what would prove it wrong** before you search (e.g. "wrong if the pricing page shows a different monthly figure or no monthly option"). A claim with no falsification test is not checkable.
3. **Open the official page** (pricing/help/changelog). Record URL, source date, access date, and what the page actually showed.
4. **Assign confidence:** HIGH = read directly from the official page this session; MEDIUM = official-domain text via a search snippet, or the page loaded but the figure did not render, or independent sources agree but the official page was not readable; UNVERIFIED = not confirmed from the official page (third-party consensus only, or no source found).
5. **Assign a verdict:** CONFIRMED (backed as written) · CORRECTED (was wrong; the copy now says the right thing) · CHALLENGED (a credible case against it stands; the copy says so) · UNKNOWN (not settled; the copy says where to find out).
6. **Write the supported wording** — the exact sentence the source supports, nothing more.
7. **Check the competing alternative** (at least one) so the claim is comparative, not isolated.
8. **Re-verify on posting day** for every price/limit; log any change and correct the copy before it ships. The verdict log is add-only: corrections are appended, never silently overwritten.

## Claim-ledger template (copy this per post)

```markdown
## Claim ledger — [post title] — last checked [date]

| # | Claim (exact wording) | Wrong if… | Source URL | Source date | Access date | Confidence | Verdict | Exact supported wording |
|---|---|---|---|---|---|---|---|---|
| 1 | | | | | | HIGH / MEDIUM / UNVERIFIED | CONFIRMED / CORRECTED / CHALLENGED / UNKNOWN | |
| 2 | | | | | | | | |
```

- One row per claim that appears in copy, on-screen text, or a visual.
- UNVERIFIED rows: the claim must NOT appear in the post as a stated figure; use the supported wording instead.
- Corrections: if a fact changes after publishing, update where possible and add a correction note. Keep the old row in the log with its verdict changed to CORRECTED — do not delete it.

## Claim-type → primary source (where to look first)

| Claim type | Primary source |
|---|---|
| Price, plan, free-tier limit | Vendor pricing page, then vendor help/billing docs |
| Feature exists / works as described | Vendor docs, changelog, or the product itself (hands-on) |
| Model availability, version name | Vendor model list / release notes |
| Platform policy, disclosure rule | Platform help centre / policy page |
| Usage limit, rate limit | Vendor docs or pricing page footnote |
| Regional availability | Vendor pricing page (region selector) or help centre |

## Worked example: an unverified list (dated snapshot, not a standing list)

The list below is a **worked example** of what an unverified list looks like — a snapshot from 15 Nov 2026, kept to show the shape, not to be quoted. Every item on it was UNVERIFIED on that date and may have been verified, changed, or discontinued since. Never copy a dated list into a post; re-check each item and build a fresh ledger.

> Example (15 Nov 2026): Gemini consumer plan prices (Plus/Pro) · NotebookLM notebook/source limits + rename date · Google Flow daily credits + Veo per-clip costs · CapCut free/pro details · Canva free plan + AI allowance + Pro price · Firefly Standard price · Leonardo free tokens + Essential price · Perplexity Pro monthly-billing figure.

What the example teaches: a good unverified list names the *exact figure* that is missing ("Pro monthly-billing figure"), not the tool in general — so the re-check has a precise target.

## Verification checklist (before a post leaves draft)

- [ ] Every price/limit has a ledger row with an official URL.
- [ ] No UNVERIFIED figure appears as a stated price, limit, or count.
- [ ] Official domain verified (no lookalike links).
- [ ] Hands-on vs desk-researched label present and true.
- [ ] "Last checked" date present.
- [ ] Sponsorship/affiliate status disclosed if any; sponsorship never determines ranking.
- [ ] Riskiest claims checked first; verdict log complete and add-only.
