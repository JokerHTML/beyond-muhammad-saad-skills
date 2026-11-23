---
name: blog-writing
description: Write long-form blog posts that are true, original, readable, and honest — research, outline, draft, edit, gate, publish, refresh.
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
---

# Blog Writing — Write Posts That Are True, Original, and Read

**Scope:** long-form blog writing (posts of ~500–5,000 words) on any platform — Blogger, WordPress, Ghost, Medium, or a static site.
**Companion skill:** `../blogger-seo-ranking/SKILL.md` — the Blogger SEO & Ranking skill is the authority for platform mechanics (setup, sitemaps, robots.txt, indexing, backlinks, canonical, tracking). This skill covers the *writing*; the Blogger skill covers the *platform*. Cross-references are by section number. Do not merge the two: a writing defect and a platform defect are fixed in different places.
**Labelling (used throughout):** **FACT** = verified from a primary/official source opened during research. **SIGNAL** = credible secondary, corroborated by more than one independent source. **SPECULATION** = single-source, opinion, or this skill's own synthesis judgement — flagged as such, never taught as fact.
**Re-verification discipline:** every dated claim in this skill carries its date. Before teaching a dated stat, policy, or platform rule, re-check the primary source listed in §11. Google Search Central pages, the SPJ Code, and Medium's AI policy all changed during 2025–2026; a 2026 citation is not a permanent fact. Re-check cycle: every 6 months, or before any training/publishing use.

## Purpose

Teach a writer — human, or human working with AI — to produce a blog post that is **true** (every factual claim sourced), **original** (it offers something the top 10 results do not), **readable** (a scanner can follow it, a reader can finish it), and **honest** (it promises only what it delivers). The workflow is research → outline → draft → edit → gate → publish → refresh, with a numbered pre-publish gate (§9) and a scored quality rubric (§10).

**The one-line test:** if you removed all the cited material from your post, would anything original remain? If the answer is no, the post is not yours — and it is not ready.

## When to use this skill

- Writing a new blog post of any type (how-to, listicle, news/trends, opinion, review, case study, explainer, comparison).
- Rewriting or refreshing an existing post.
- Reviewing a draft someone else (or an AI) wrote.
- Deciding whether a post idea is worth writing at all (the information-gain test, §3).
- Writing with AI assistance without producing AI slop.

**Do NOT use this skill for:** short-form social copy; platform setup or technical SEO (use the Blogger SEO skill); video scripts; email copy.

## Hard rules

Non-negotiable. A post that breaks one is not ready, however good it reads.

1. **Never invent a fact, a number, a quote, a source, or an example.** If you cannot name the source, delete the sentence or find the source. There is no third option.
2. **Never present an unverified claim as fact.** Unverified claims are cut, verified, or labelled as unconfirmed — in the body, not in a footnote.
3. **Never copy text without attribution.** Direct copying, mosaic stitching, and inadequate paraphrase are all plagiarism.
4. **Never write a title the post does not deliver.** The title-truth test (§4) is a gate item, not a guideline.
5. **Never fabricate an author, a credential, or a testimonial.** **FACT** (Google, October 2026): fabricated author profiles are an explicit low-quality signal.
6. **Never publish without the gate.** The pre-publish gate (§9) is run in full, every time. One CRITICAL failure = do not publish.
7. **Never use a detector score as a quality decision.** Detectors measure perplexity and burstiness, not authorship — and they are systematically biased against non-native English writers. Liang et al. 2023 (*Patterns* 4(7)): 61.22% average false-positive rate on 91 human-written TOEFL essays across seven detectors; 19.8% flagged by all seven; near-perfect accuracy on native-speaker essays. **FACT** (peer-reviewed, verified 2026-11-23).
8. **Never re-date a post without a real edit.** A refresh must be a substantive change with a visible "Last updated: [date]" note. Re-dating without a real change is a warning sign (**FACT** — Google).
9. **Never teach an unverified item as fact.** Anything in the unverified list (§12) stays unverified until it is checked with its stated method.
10. **Never let AI write the post unsupervised.** The human owns the thesis, the research, the evidence, the voice, and the decision to publish. AI is a drafting assistant, not an author.
11. **Visuals — verified first, labelled always.** Use as many to-the-point visuals as the article can carry — one per section/claim where a visual genuinely adds information (a screenshot, a diagram, a chart, a real example). Every visual is verified against its source and carries its own descriptive alt text and its own clear source/credit line. **Real photos first:** use real photos wherever they exist, freely licensed only (e.g. Wikimedia Commons — verify the licence on the file page, credit photographer + licence visibly). Never a fan-made, leaked, or unverified image; never a news-outlet photo you do not have rights to. **Extra visuals** beyond verified references may be used only when they are a clear hit that will boost the article — and each carries a visible disclaimer stating exactly what it is (e.g. "Illustrative image — not an official screenshot", "AI-generated illustration"), sitting with the image, never hidden in a footnote. **Fallback:** if no reference image can be found anywhere but the visual is important, generate it with a capable image model at the highest available quality (example: Google Gemini, Pro / Nano Banana Pro tier, explicitly selected), labelled with the visible "AI-generated illustration" disclaimer. A generated image is never presented as a real photo or an official image. Quantity never overrides relevance: a decorative image that adds nothing is a defect, and a section with no fitting verified visual goes without one. Record every visual (file + placement + alt text + credit + disclaimer, if any). A visual that cannot be recorded is not ready to publish.

## 1. The workflow — research → outline → draft → edit → gate → publish → refresh

| Step | What happens | Output |
|---|---|---|
| **1. Decide** | Thesis in one sentence · reader defined · intent matched to the SERP · information-gain test (what do you offer that the top 10 don't?) · 0 gain = do not write | One-sentence thesis + go/no-go decision |
| **2. Research** | Read sources before drafting · build the claim sheet (every factual claim → primary/secondary source → date → status) · triangulate load-bearing claims | Claim sheet, 100% verified before drafting |
| **3. Outline** | Thesis-first MECE outline · H2s tell the whole story · direct answer placed first · type template applied (§5) | Outline with H2s that pass the read-only-H2s test |
| **4. Draft** | Write from the outline + claim sheet · answer first (BLUF) · one idea per paragraph · title + H1 + og:title written as three separate fields · Key Takeaways box (§4.7) | Full draft with three titles |
| **5. Edit** | Four passes in order: structural → line → copyedit → proofread · read aloud · check every link and every number against the claim sheet | Edited draft |
| **6. Gate** | Pre-publish gate (§9: 22 flaws) + scored rubric (§10) + Blogger SEO gate for platform defects | Gate record: pass/fail per flaw + score |
| **7. Publish** | Permalink set before publishing · meta description · labels · images + alt text · byline · disclosure where required · verify live | Live post, verified on the public URL |
| **8. Refresh** | Re-verification trigger set for every time-sensitive claim · when it fires, re-verify and update honestly, or mark the post outdated | Update log entry |

Skipping a step is breaking a rule. A post that skipped research, the gate, or the live check is not ready. **Optional Step 0 (Discover)** — a daily trending-first variant — lives in Appendix A. It is not part of the core workflow.

## 2. The brief — write it before you research

Every post starts with a brief, one page, before any research:

- **Thesis:** one sentence. What does this post prove, teach, or answer?
- **Reader:** one sentence. Who is this for, and what do they already know?
- **Intent:** informational / commercial investigation (navigational and transactional are not blog posts).
- **Angle:** what makes this post different from the top 10? (Impact / Originality / Credibility / Timeliness — SIGNAL.)
- **Primary keyword:** one. **Secondary keywords:** 3–8. ($0 keyword method: Blogger skill §2.)
- **Type:** one of the eight templates (§5).
- **Evidence needed:** what first-hand evidence, data, or examples must this post contain to be worth writing?
- **Audience locale (fill in, do not assume):** language variant, currency, units, and source geography for [your audience]. See Appendix A for a worked localisation variant. The default is the audience you actually serve — never a borrowed one.

**If you cannot fill in the brief, you do not have a post yet.** Do not research until the brief exists — research without a thesis produces a pile of facts, not an argument.

## 3. The information-gain test — the go/no-go decision

**Backlinko's question (SIGNAL):** "What do you have to offer that the top 10 results don't?" Before drafting, read the top 10 results for the primary keyword and answer it in writing. Acceptable answers:

- A first-hand test or experiment nobody else has run.
- Data nobody else has (your own survey, your own logs, your own measurements).
- A clearer explanation of a confusing topic.
- A correction of a common error in the top 10.
- A more complete answer (a missing section, a missing edge case, a missing caveat).

**If the honest answer is "nothing", do not write the post.** A post that adds nothing is thin content — and thin content is a spam-policy concern (**FACT** — Google). Write a different post, or find the gain first.

## 4. Titles — the first contract with the reader

4.1 **Three titles, written separately:** SEO title (50–60 chars) · H1 (40–70 chars, reader-facing) · og:title (≤60 chars, self-contained). Then check they agree — matching title + H1 is the best defence against Google rewriting.
4.2 **Google rewrites most titles.** Zyppy (Cyrus Shepard, data Q1 2022, 80,959 titles across 2,370 sites, desktop): Google rewrote **61.6%** of titles; titles of 51–60 characters were rewritten least (39–42%); titles over 70 characters were rewritten 99.9% of the time. **Update:** McAlpin's Q1 2025 study (24,886 results) found a **76.0%** rewrite rate — the rate is rising, not falling. Treat both figures as dated measurements (SIGNAL), not permanent constants. You cannot control the display. You can only write a good title and make your page's other title sources agree with it.
4.3 **Truncation is pixels, not characters** (~600px desktop, SIGNAL). There is no "70-character limit" and no "15–40 characters is best" rule. Both are folklore.
4.4 **Use a formula that matches the post's intent and the promise you can keep.** Ranked formula families: how-to ("How to [do X]"), list ("[N] [things] that [outcome]"), question ("[Question]?"), comparison ("[A] vs [B]"), guide ("The complete guide to [X]"), mistake ("[N] mistakes [audience] makes with [X]"), data ("[X] in [year]: what [data] shows"). A formula that over-promises is clickbait. **Title-truth test (gate item):** read the title, then read the post. Every word in the title must be true, present, and proportionate in the post. A number in the title must match the count in the body exactly.
4.5 **Numbers, emotion, curiosity:** numbers help when the post genuinely contains that many items; emotion must match the topic; the curiosity gap is the *unanswered question*, not the withheld fact. The following are **unverified — do not teach them**: "odd numbers outperform even by ~20%", "brackets boost CTR by ~33%", "80% read only the headline" (Ogilvy), "testing 5–7 headline variants finds the optimal headline in 83% of cases". A previous draft of this skill also stated that numbers survive rewriting 97.3% of the time when present in both title and H1 — that figure could not be traced to any source and has been **cut**.
4.6 **Write 6–8 variants, pick 1.** The advice is practitioner judgement (SPECULATION); there is no verified "optimal number of variants" statistic.
4.7 **AI-citation readiness (adopted from the best surveyed skills).** AI assistants and AI Overviews cite pages that are easy to quote: put the direct answer in the first 100 words, add a **Key Takeaways** box (3–5 bullets, each a self-contained factual sentence with its source), keep one citable fact per paragraph, and make every H2 a question the section answers. No special file, schema, or markup is needed for AI search (**FACT** — Google, "AI features and your website", last updated 2025-12-10: "There are no additional requirements to appear in AI Overviews or AI Mode").

## 5. Structure — the spine every post shares

1. **Thesis** — one sentence.
2. **Answer first (BLUF)** — the direct answer in the first 100 words, and each section's answer in its first sentence. **FACT** (NN/g, Nielsen 1997): 79% of users scan; 16% read word-by-word. Readers read ≤28% of the words on a page (Nielsen 2008, 45,237 page views).
3. **MECE outline** — sections mutually exclusive, collectively exhaustive (SIGNAL).
4. **One idea per section, one idea per paragraph** — each opens with its claim, then its evidence, then its implication.
5. **Close the loop** — the conclusion returns to the thesis and names the next step. It adds nothing new.

**Length:** there is **no preferred word count** (**FACT** — Google). Length follows completeness. Per-type planning ranges below are **SPECULATION** — syntheses of practitioner guides, not measurements. The better method: sample the live SERP per query and let the query set the length.

**Eight type templates** (purpose · intent · H2 flow · headline pattern · planning range · evidence requirement · #1 flaw):

| Type | Planning range* | Evidence required | #1 flaw |
|---|---|---|---|
| How-to | 1,000–2,500 | Steps you actually performed, with screenshots/results | Steps that cannot be followed as written |
| Listicle | 1,200–2,500 | Every item verified; no padding to hit the number | Padded items |
| News/trends | 500–1,500 | Primary source for every news claim; date on every claim | Reporting rumour as fact |
| Opinion | 800–1,500 | Reasoning visible; counter-argument addressed | Opinion dressed as fact |
| Review | 1,000–2,500 | First-hand use; what you tested, for how long | Reviewing without using |
| Case study | 1,500–3,000 | Real numbers with context; what failed, not only what worked | Cherry-picked results |
| Explainer | 1,000–2,500 | Definitions traced to authoritative sources | Jargon without explanation |
| Comparison | 1,200–2,500 | Same criteria applied to each option; hands-on where possible | Comparing on different criteria |

\* Planning ranges only. The comparison template was built from practitioner consensus, not independently corroborated — treat its range as the weakest of the eight.

**Readability scores** (Flesch, Flesch-Kincaid) measure only sentence length and syllables. Use them as a per-section diagnostic, never a quality target. Do not teach a target grade.

## 6. SEO writing — people-first, with the mechanics that matter

1. **People-first is the governing rule (FACT).** Google's framing question: "Why was this created?" A post written primarily to rank fails the test regardless of its keyword placement.
2. **No separate helpful-content system since March 2024 (FACT).** It was folded into core ranking. There is no helpful-content score to game.
3. **Intent matching beats keyword placement (SIGNAL).** Read the SERP before drafting; the top 10 tell you the intent, the format, and the depth the query expects.
4. **Meta description is NOT a ranking factor (FACT, since 2009).** Its job is to earn the click. Google rewrites it most of the time — Ahrefs (2020, 20,000 keywords, 192,656 pages): **62.78%** rewritten; corroborated by Portent (2020: 68% desktop, 71% mobile) and Seer Interactive (2025: ~70%). Dated measurements (SIGNAL), direction consistent.
5. **E-E-A-T is a quality-rater concept, not a ranking factor (FACT).** There is no E-E-A-T score. Show experience, expertise, and trustworthiness *in the content* — a bio does not compensate for a shallow post.
6. **Main content is judged on effort, originality, talent, and accuracy (FACT — Google, October 2026).** The pre-publish gate (§9) is built on exactly these four words.
7. **AI content is not banned (FACT).** Scaled content abuse is purpose-based, not method-based. A single AI-assisted post written for the reader is fine; a hundred AI-generated posts targeting keyword variations is not.
8. **No additional requirements for AI Overviews / AI Mode (FACT — Google, December 2025).** No llms.txt, no special schema. The same people-first guidance applies.
9. **SEO takes hours to months (FACT).** Do not rewrite a post because it has not ranked in three days.

## 7. Research, sourcing & editing — the evidence discipline

1. **Research before drafting.** The claim sheet is built before the draft is opened. A draft written from memory will contain claims you cannot source.
2. **Claim sheet format (one row per factual claim):** claim (verbatim) · source (Tier 1 = the original record; Tier 2 = authoritative secondary, noted as second-hand; Tier 4 = background only; Tier 5 = never cited) · source date · status (Verified / Unverified) · triangulation (second independent source for load-bearing claims). A source is not a source if you have not opened it. An AI summary of a source is not the source.
3. **Triangulate load-bearing claims.** A price, a statistic, a date, or a policy needs two independent sources — not two pages citing the same source.
4. **SIFT before you trust a claim:** Stop · Investigate the source · Find better coverage · Trace to the original context (Caulfield 2019; Stanford Wineburg & McGrew 2019 — SIGNAL).
5. **Fact-check workflow:** isolate the testable claim → ask a neutral query → triangulate → read the explanation, not the rating → show your work (link to the source in the post).
6. **Quoting:** never alter a quote; "said" is the preferred attribution verb; anonymous sources are a last resort (SPJ Code of Ethics, revised 4 October 2026 — **FACT**, verified 2026-11-23).
7. **Plagiarism includes mosaic and inadequate paraphrase.** If you removed all cited material, would anything original remain? If no, the post is not yours.
8. **Four editing passes, in order:** structural → line → copyedit → proofread. Do not copyedit a draft you are about to restructure. Read aloud. Leave a gap between passes where possible (same-day vs next-day pass separation is SPECULATION — untested for solo bloggers; record which you did).
9. **Correct errors promptly and visibly** — a correction note at the top of the post, not a silent edit. Disclose conflicts of interest in the first two paragraphs.

## 8. AI-assisted writing — use AI without producing slop

1. **Google judges quality, not AI use (FACT).** Appropriate use of AI is not against the guidelines; manipulating rankings with automation is.
2. **Detectors measure perplexity and burstiness, not authorship.** Never use a detector score as a quality gate (see hard rule 7).
3. **Slop signals (B1–B8):** hollow vocabulary · empty connectors · formulaic transitions · rule-of-three · negative parallelism ("not X — it's Y") · em-dash overuse (≤1–2 per article, SPECULATION) · bold-first bullets · hedging/weasel words. Probabilistic — a single instance proves nothing; a pattern throughout is slop.
4. **Two tests catch slop better than any list:** the one-sentence-summary test (can you summarise the post in one sentence specific to *this* post?) and the anywhere-company test (could this post have been written by anyone, about anything, with only the nouns changed?).
5. **Disclosure (Medium AI content policy, FACT — primary page opened, updated 2026-11-11, verified 2026-11-23):** majority-AI text disclosed in the first two paragraphs and cannot be paywalled; AI images captioned; outlining/grammar/fact-checking needs no disclosure. Note: this is Medium's policy, not a universal law — on your own blog, disclose by the same standard as a trust rule, not because a platform forces it.
6. **Human-in-the-loop, 8 stages:** brief → research → outline → draft → human rewrite → fact-check → slop sweep → final read-aloud. Five hard gates: thesis · evidence · originality · slop · voice. Any one fails = do not publish.

## 9. Pre-publish gate — 22 flaws

**22 flaws: 8 CRITICAL / 9 HIGH / 5 MEDIUM.** One CRITICAL failure = do not publish. HIGH failures must be fixed or explicitly accepted in writing with a reason. MEDIUM: fix if possible; at most two may ship, with the reason recorded. Work through the flaws in order; run the detection check, do not rely on memory. This gate covers **writing quality only** — run the Blogger SEO skill's own 20-flaw gate (blogger-seo-ranking §10) too for platform defects. The two gates are complementary, not alternatives.

### CRITICAL

| # | Flaw | Detection check | Fix |
|---|---|---|---|
| C1 | Unverified factual claim | Every claim-sheet row = Verified with a Tier 1/2 source + date; any Unverified row fails | Verify (two sources for load-bearing) or delete the sentence |
| C2 | Fabricated or untraceable number | Follow every number's citation chain to the primary source; check rounding did not change meaning | Replace with the sourced figure + context (sample, date, scope) or delete |
| C3 | Plagiarism (direct, mosaic, inadequate paraphrase) | Read post against sources; search distinctive phrases; ask: without cited material, does anything original remain? | Rewrite from understanding, or quote properly with attribution |
| C4 | Title does not match the post | Title-truth test (§4.4): every word true, present, proportionate | Rewrite the title — never rewrite the post to match a misleading title |
| C5 | Altered or unattributed quote | Compare every quote word-for-word with its source; attribution names speaker + source, in text, with link | Restore exact wording, or paraphrase outside quotation marks |
| C6 | Fabricated author credential or fake byline | Is the byline a real person? Are credentials verifiable? Is AI authorship disclosed where it matters? | Real byline with verifiable credentials, or no credential claim |
| C7 | Spam-policy violation | Read aloud: written for a search engine, not a reader? Keywords repeated unnaturally? Anything hidden? | Rewrite for the reader; if the post exists only to target a keyword, do not publish |
| C8 | Visual presented as real when it is not | For every visual: what is it, and does the post say so honestly? Reference unclear/unverified/fan-made/leaked fails; generated image without its label fails | Remove, replace with a verified reference, or label it visibly as what it is |

### HIGH

| # | Flaw | Detection check | Fix |
|---|---|---|---|
| H1 | Load-bearing claim with a single source | The 2–3 claims the thesis depends on each need two independent sources | Find a second source, or downgrade the claim ("According to [source]…") |
| H2 | Stale source | Check the date on every source; for fast-moving topics, >12 months old is suspect; re-open and confirm it still says what the post claims | Find a current source, or label the figure with its date |
| H3 | Missing disclosure | List every commercial relationship + AI contribution; each must be disclosed where the reader sees it before acting | Add the disclosure (§8.5) |
| H4 | Number in the title does not match the body | Count: title number = H1 number = items in the body | Change the title, or add/remove a genuine item — never pad |
| H5 | No direct answer in the first 100 words | Read the first 100 words: can a reader state what the post answers? | Move the direct answer to the top |
| H6 | Broken or misdirected link | Click every link: must load and be the page the text describes | Correct the URL or remove the link |
| H7 | Opinion presented as fact | Scan for conclusions stated without evidence | Add evidence, or reframe as opinion with reasoning visible |
| H8 | Section with no evidence | For each H2: what evidence does it offer? None = assertion, not argument | Add evidence, merge, or cut |
| H9 | Extra visual without its disclaimer | Every visual beyond verified references must state what it is in its caption/credit line; check the visual record | Add the disclaimer with the image, or remove the visual |

### MEDIUM

| # | Flaw | Detection check | Fix |
|---|---|---|---|
| M1 | Readability failure in one section | One section far harder than the rest — wall of text, unbroken long sentences, unexplained jargon | Break paragraphs, shorten sentences, explain jargon, add a subheading |
| M2 | CTA before value, or multiple competing CTAs | First CTA: has the post delivered its core value by then? Count CTAs — one primary | Move CTA after the value; demote/remove secondary CTAs |
| M3 | Image without useful alt text or recorded reference | Alt text must describe what the image shows; every visual must be recorded | Write descriptive alt text; record the reference. Decorative images get empty alt (`alt=""`) — correct, not a failure |
| M4 | No conclusion, or a conclusion that adds new material | Does the conclusion restate the thesis and name the next step? New material = incomplete outline | Close on the thesis, or move the new material into the body |
| M5 | Meta description over-promises or is missing | Read the description against the post: ~140–160 chars, no exaggeration | Write or rewrite it. Not a ranking factor (FACT, since 2009) — but it is the click |

### Non-flaws — do NOT fail a post for these

Flesch score below an arbitrary threshold · post shorter than a word-count target · no keyword in the first 100 words · fewer than N headings, or headings in non-standard order · no keyword in the meta description · no "power word" or number in the title · written with AI assistance (undisclosed AI generation and AI slop are the defects, not assistance) · topic a competitor already covered · no image (an image that adds nothing is worse than none) · no generated/AI visual · not published on a fixed schedule.

## 10. Scored quality rubric — 100 points

A post must pass the gate **and** score **≥85/100** to publish. The threshold is this skill's own rule (**SPECULATION — synthesis judgement**); it is not a measured or published standard. Score each dimension honestly — a dimension you cannot evidence scores 0.

| Dimension | Points | What earns full marks |
|---|---|---|
| Accuracy & evidence | 25 | Every factual claim sourced to a primary source; load-bearing claims triangulated; claim sheet 100% verified; no stale sources; numbers traced to primary source with context |
| Depth & completeness | 20 | Thesis answered completely; passes the information-gain test; edge cases and caveats included; nothing essential missing |
| Structure & flow | 15 | Thesis-first MECE outline; answer-first at post and section level; H2s tell the whole story; one idea per paragraph; conclusion closes the loop |
| Usefulness | 10 | Reader can act on the post — a step to take, a decision to make, a question answered. No actionable value = 0 |
| Originality | 10 | First-hand evidence, a new angle, a correction, or a clearer explanation — something the top 10 do not offer |
| Readability & voice | 10 | Scannable (short paragraphs, descriptive headings, lists where they help); reads aloud in the author's voice; no slop pattern |
| SEO mechanics | 5 | Title/H1/og:title written and matched; meta description honest; internal + external links relevant and working; images have descriptive alt text and follow hard rule 11 |
| Accessibility & honesty | 5 | Disclosure where required (including visual disclaimers); byline real; no misleading title, description, or claim; corrections policy followed |
| **Total** | **100** | **Pass bar: ≥85 AND zero CRITICAL gate failures** |

**Scoring notes:** a post that passes the gate but scores 70–84 is a *good draft*, not a publishable post — fix the weakest dimension and re-score. A post that scores ≥85 but has a CRITICAL gate failure does not publish. The gate outranks the score. Record the score and the gate result with the post — the score is the audit trail for the next refresh.

## 11. Myths to ignore — folklore this skill does not teach

This table and the Blogger skill's §12 myths table were cross-checked on 2026-11-23 and agree on every overlapping row (meta description, E-E-A-T, word count, AI content, duplicate content, freshness, custom domain, Blogspot). Where they overlap, the wording below is the harmonised version; neither table contradicts the other.

| Myth | Status | What is true instead |
|---|---|---|
| "A blog post must be 1,500 / 2,000 / 2,500 words" | **False** (FACT — Google: no preferred word count) | Length follows completeness |
| "The average first-page post is 1,447 words, so write 1,447 words" | **Misleading** (SIGNAL — top-10 average, "no direct relationship" with ranking; Backlinko 11.8M-result study, primary page not re-opened — see §12) | An average is not a target |
| "Meta description is a ranking factor" | **False** (FACT — not a ranking factor since 2009) | It earns the click |
| "Keyword density should be 1–2%" | **False** (no published rule) | Write naturally; Google understands synonyms (FACT) |
| "Keyword must appear in the first 100 words" | **False** (no published rule) | Answer first because the reader needs it |
| "E-E-A-T is a ranking factor / you have an E-E-A-T score" | **False** (FACT — quality-rater concept, no score) | Show experience and trustworthiness in the content |
| "AI content is banned / penalised" | **False** (FACT — scaled content abuse is purpose-based) | AI-assisted content is fine if people-first and original |
| "You need llms.txt / special schema for AI search" | **False** (FACT — Dec 2025: no additional requirements) | Same people-first guidance applies |
| "Longer content always ranks better" | **False** (FACT — no preferred word count) | Completeness + reader satisfaction |
| "Duplicate content is penalised" | **False** (FACT — not a penalty; Google picks a canonical) | Cross-posting discipline still matters (Blogger skill §8) |
| "Freshness = change the date" | **False** (FACT — re-dating without real change is a warning sign) | Real edit + visible "Last updated" note |
| "The 70-character title limit" | **False** (pixels, not characters) | 50–60 chars, lowest rewrite rate (SIGNAL — Zyppy 2022) |
| "80% read only the headline" (Ogilvy) | **Unverified** (no primary source located) | Do not teach it |
| "Odd numbers outperform even by ~20%" | **Unverified** (no primary Conductor study located) | Do not teach it |
| "Brackets boost CTR by ~33%" | **Unverified** (not on the cited page) | Do not teach it |
| "Flesch ≥ 60 = good writing" | **Outdated** (Yoast 19.3 changed the model) | Diagnostic only |
| "Post daily for SEO" | **False** (no published rule) | Publish when the post is ready and verified |
| "Google uses GA data in rankings" | **False** (FACT — Google states it does not) | Do not teach it |
| "Blogspot is penalised" | **False** (FACT — no platform penalty) | Platform choice is a features decision |
| "Custom domain = ranking boost" | **False** (no published boost) | A custom domain is a branding decision |

## 12. Official references & what could not be verified

- Google Search Central — "Creating Helpful, Reliable, People-First Content" — https://developers.google.com/search/docs/fundamentals/creating-helpful-content
- Google Search Central — "SEO Starter Guide" — https://developers.google.com/search/docs/fundamentals/seo-starter-guide
- Google Search Central — "Influencing your title links in search results" — https://developers.google.com/search/docs/appearance/title-link
- Google Search Central — "AI features and your website" (last updated 2025-12-10) — no additional requirements for AI Overviews / AI Mode
- Google Search Central — Spam policies (scaled content abuse) — https://developers.google.com/search/docs/essentials/spam-policies
- Google Search Central — "Write high quality reviews" — https://developers.google.com/search/docs/specialty/ecommerce/write-high-quality-reviews
- Society of Professional Journalists — Code of Ethics (revised 4 October 2026) — https://www.spj.org/spj-code-of-ethics/
- Medium — AI content policy (updated 2026-11-11) — https://help.medium.com/hc/en-us/articles/22576852947223-Artificial-Intelligence-AI-content-policy
- NN/g — "How Users Read on the Web" (Nielsen, 1997) and "How Little Do Users Read?" (Nielsen, 2008)
- Liang et al. (2023) — "GPT detectors are biased against non-native English writers", *Patterns* 4(7) — https://doi.org/10.1016/j.patter.2023.100779
- Zyppy — "Google Rewrites 61% of Page Title Tags" (Cyrus Shepard, data Q1 2022) — https://zyppy.com/seo/google-title-rewrite-study/
- Ahrefs — "How Often Does Google Rewrite Meta Descriptions?" (2020; 20,000 keywords) — https://ahrefs.com/blog/meta-description-study/
- Backlinko — "We Analyzed 4 Million Google Search Results" (2019, updated 2025-04-16) — https://backlinko.com/google-ctr-stats

**Unverified — do not teach as fact (each needs its stated check before use):** the "80% headline" Ogilvy claim (no primary source); odd-number +20% (no Conductor study located); brackets +33% CTR (not on the cited page); headline-variant "83% optimal" (no meta-analysis located); Backlinko 1,447-word top-10 average and HubSpot/Semrush length figures (secondary summaries only — open the primary pages and record sample, date, and method first); Ahrefs AI-Overview length study (Dec 2025, 174,048 pages — secondary summaries only); Orbit Media 2025 blogger survey figures (secondary summaries only); the Feb 2026 Google Discover core update (Google's own announcement not opened); the comparison-template corroboration (§5); the solo-blogger editing-gap recommendation (§7.8); the IFCN Code wording (read via a signatory republication, not the IFCN site itself); Google's Feb 2023 AI-content post verbatim (position confirmed via the helpful-content page; the post itself not opened). The Blogger skill's own unverified list (blogger-seo-ranking §14) is incorporated by reference — do not teach any of those items as fact either.

## 13. Limits — what this skill does not do

- **Platform mechanics are out of scope.** Blogger setup, sitemaps, robots.txt, indexing, backlinks, canonical discipline, and tracking routines are the Blogger SEO skill's job. Do not re-teach them here.
- **No short-form social copy.** Hook windows, character limits, and platform-native formats belong to a social-post system.
- **No word-count targets.** There is no verified word-count rule for any post type. Per-type ranges in §5 are planning estimates (SPECULATION).
- **The ≥85/100 threshold is this skill's own rule**, not a measured or published standard. It exists to force an honest judgement.
- **No promise of rankings, traffic, or clicks.** This skill promises a post that is true, original, readable, and honest. Rankings follow from quality over time — they are not guaranteed by any checklist.
- **Tool-agnostic, $0 throughout.** No paid tool is required for any step. Where a surveyed guide is tool-locked, this skill gives the manual method.

## Appendix A — Optional variants (not hard rules)

These were owner-specific rules in the source skill. They are useful in the right context and wrong as defaults. Adopt one only by an explicit decision, recorded with the post brief — never silently.

**A1. Audience localisation variant.** Pick one audience and write everything for it: language variant, currency, units, search-intent wording, and source geography in titles, descriptions, and H2s; explain any out-of-audience context, never assume it. Example: a US + international audience means US English, $ prices, US units, US sources first, times in ET. The audience is a brief decision (§2), not a permanent property of the skill.
**A2. Trending-first Discover variant (optional Step 0).** Check a trending source first each day (e.g. X/Twitter trending + news search corroboration), cover the hottest topic the same day, and track upcoming events 7 days out / 30 days ahead. A trend is a topic, not a fact — hard rules 1–2 still bind; trending chatter alone never ships as fact. Do not adopt this variant if your blog's promise is evergreen depth: same-day trend coverage and slow, verified writing pull in opposite directions.
**A3. Event-coverage variant.** Cover an event before it peaks, as a complete guide (what it is, how to prepare, what to do, what to avoid), with visuals at every step. Cover every event you commit to — but commit deliberately: "every single event, no event too small" is a staffing decision, not a writing rule.
**A4. Coverage-scope & verification tiers (optional, for news/health/games blogs).** Tier A — verified-only, no "reported" escape hatch: politics, health benefits, diet plans, medical research, technology research claims. Tier B — labelled-unconfirmed allowed, never as fact: games rumours/leaks, trends, fashion, entertainment (label "unconfirmed"/"reported" with the source named, in the body, never in the headline as fact). Sensitive topics: cover only if brand-safe; when in doubt, skip.
**A5. Fashion-photoshoot variant.** For fashion visuals: professional-photoshoot level — the outfit worn by a model in the real environment where it looks best, never a plain studio backdrop — so the reader can see the setting it belongs to. Seasonal dressing guides stay current with the season and are refreshed when the season turns.

## Changelog (publish history)

- **v1.0.0 — 2026-11-23:** Publishable universal version. Reconciled the three source mismatches (see UPGRADE-NOTES.md): 22-flaw gate (not 20), 11 hard rules + optional variants (the source's rule 12 was owner-specific), 8-step core workflow + optional Step 0 (the source's step 0 was owner-specific). Owner-specific entries neutralised or moved to Appendix A. Dated stats re-verified (Zyppy, Liang, Ahrefs, NN/g, SPJ, Medium, Google AI-features page); the untraceable "97.3%" title-number claim cut; McAlpin 2025 title-rewrite update added. AI-citation readiness (§4.7) adopted from the best surveyed skills. Myths tables cross-checked with the companion skill and harmonised.
