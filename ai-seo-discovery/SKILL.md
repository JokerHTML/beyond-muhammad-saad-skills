---
name: ai-seo-discovery
description: Find the exact words the audience already searches for, match each post to one searchable phrase + intent, and produce the per-post SEO output — without inventing keyword data.
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
---

# AI SEO Discovery

## Purpose

Find the exact words the audience already searches for, match each post to one searchable phrase + intent, and produce the per-post SEO output — without fake GEO/AEO hacks, invented keyword volumes, or guaranteed-ranking claims.

## When to use

- Before drafting any post.
- When choosing a Top 5 topic, tutorial angle, or news headline.
- Post-publication review (query/performance check where analytics are readable).

## Rules (hard)

- **Never invent keyword volume, difficulty, or ranking data.** If no tool measured it, write "unmeasured — chosen from audience wording" and do not quote a number. A volume estimate is only ever quoted with the tool, the date, and the exact figure the tool showed.
- **Never sell a GEO/AEO hack, secret ranking factor, or guaranteed inclusion in AI answers.** Foundational SEO still matters for AI search; there is no shortcut to buy.
- **One primary phrase per post.** Secondary phrases only if genuinely relevant (3–8 max).
- **Hashtags 1–3 where they genuinely help, never stuffed.** LinkedIn 0–1. IG cap 5.
- **Classify intent from the query's language, not from guesswork.** Read the modifiers: "how to" = do; "best X for Y" / "vs" / "review" = compare; "what is" = learn; "buy" / "price" / "discount" = buy; "fix" / "not working" = troubleshoot.
- Every claim about a platform's search behaviour must trace to an official source (see references) or be labelled as the author's own observation.

## The framework: 4 stages

Adopted from the best comparable workflows and tightened with the no-invention rule:

1. **Discover** — cast a wide net from seed terms, the audience's own wording, competitor phrasing, and Search Console queries for a site you own. Aim for a broad candidate list; narrow later.
2. **Classify** — every candidate maps to one intent. Get this right or the rest is noise.

   | Intent | Signals | Content type that wins |
   |---|---|---|
   | Learn | what is, why, guide, explained | Explainer, guide, FAQ |
   | Compare | best, vs, review, top, alternative | Comparison, Top 5, ranking |
   | Do | how to, tutorial, steps, with | Tutorial, walkthrough, template |
   | Buy | price, buy, discount, deal | Pricing page, offer, review with price |
   | Troubleshoot | fix, not working, error, won't | Fix guide, checklist |

3. **Cluster** — group related phrases into one topic cluster per post. One cluster, one post. A phrase that belongs to two clusters is two posts, not one post doing both jobs.
4. **Prioritise** — rank candidates by native evidence (what autocomplete, search suggestions, and your own analytics actually showed) and intent match. If real volume/difficulty data exists from a keyword tool, score with `Opportunity = (Volume × Intent Value) / Difficulty` (Intent Value: learn 1, compare 2, do 2, buy 3, troubleshoot 2). If no real data exists, do **not** run the formula — rank by evidence strength instead and say so.

## Learning modules

1. **Keyword + search intent:** audience wording, query variations, questions, comparisons ("best X for Y"), long-tail queries, content gaps.
2. **Platform-native search:** Instagram search; YouTube Search/Studio; Pinterest trends/search; Threads/X topical language. TikTok Creator Search Insights — only usable with an active TikTok account; if unavailable, mark it unavailable, never claim it.
3. **YouTube SEO:** topic intent, title clarity, thumbnail promise, description, chapters, spoken keywords, captions; tags only where genuinely useful. Shorts-specific placement (title formulas, hashtag line, Tags field) is governed by the youtube-shorts-seo skill where it exists — this skill's caps do not override it. See "Alignment with the Shorts SEO skill" below.
4. **Instagram/Facebook:** discoverable phrasing, accurate captions, topic consistency, original media, alt text, compliant hashtags.
5. **Pinterest SEO:** keyword-led pin title (keyword in first 40 of 100 chars), natural description ≤800 chars via scheduler (≤500 if the pin may be edited by hand in the app), vertical 1000×1500 asset, destination relevance, board context.
6. **X/Threads:** clear topical language, strong first line, concise context, useful source links, conversation relevance.
7. **Web/Google SEO:** people-first content, helpful structure, original analysis, descriptive titles, technical accessibility, Search Console measurement (free service).
8. **AI-search literacy:** foundational SEO still matters; no fake GEO/AEO hacks.
9. **Optimisation after publish:** Search Console + platform analytics, query/page/post outcomes, CTR, retention, saves, shares, clicks, conversions.

## Process (7 steps)

1. **Start from the audience problem**, not a keyword tool. Write the question a beginner would type, in their words.
2. **Generate variants:** question form, comparison form ("X vs Y"), "best X for Y", "how to X with Y", task + tool form.
3. **Check the phrase natively:** YouTube Search autocomplete, Pinterest search suggestions, Instagram search, Google Search Console queries for a site you own. Record what you actually saw and the date. A phrase with no native evidence is a guess — label it as one.
4. **Pick one primary phrase** (the variant with the clearest intent match + most native evidence) and 3–8 secondaries.
5. **Place it:** line 1 of the caption/post (IG first 125 chars, Threads 101–150, X first 71–100, FB first ~80, LinkedIn hook ≤40 chars, Pinterest title first 40 chars), on-screen headline, opening spoken phrase for video.
6. **Write alt text** for every meaningful image; accurate captions/subtitles for video.
7. **Verify every link destination** before delivery; record the check date.

## Per-post SEO output (required — paste into every plan)

- Primary search phrase + reader intent (learn / compare / do / buy / troubleshoot).
- 3–8 secondary phrases or natural variants.
- Platform-native title/headline + caption/description.
- On-screen headline + opening spoken phrase (video).
- 1–3 hashtags where they genuinely help.
- Alt text (images) / captions (video).
- Verified link destination + source references.
- Post-publication review note (what to check at 24h / 72h / 7d).

## Alignment with the Shorts SEO skill

This skill and the youtube-shorts-seo skill in the same collection govern different surfaces and do not contradict:

- **Feed/social posts (this skill):** IG ≤5 hashtags, LinkedIn 0–1, other platforms 1–3 where they help. Hashtags are a minor discovery aid.
- **YouTube Shorts descriptions (youtube-shorts-seo skill):** the hashtag line is a fixed, locked format (up to 6 tags, channel tags + moment tag). That skill governs Shorts; this skill defers to it there.
- **Tags field (YouTube):** fresh per video, specific → variants → channel tags last. Neither skill permits a comma-separated keyword wall in a description.

If the two skills ever disagree on a specific video, the Shorts skill wins for that Shorts video, and the disagreement is logged, not silently resolved.

## Official references (re-check before applying any time-sensitive rule)

- Google Search Central — helpful content: https://developers.google.com/search/docs/fundamentals/creating-helpful-content
- Google Search Central — AI-optimization guide: https://developers.google.com/search/docs/fundamentals/ai-optimization-guide
- Google Search Central — gen-AI content guidance: https://developers.google.com/search/docs/fundamentals/using-gen-ai-content
- YouTube Help — Shorts search/discovery: https://support.google.com/youtube/answer/11914225
- YouTube Help — content performance for recommendations: https://support.google.com/youtube/answer/16559650
- Instagram Creators best-practices hub (Meta): https://about.fb.com/news/2024/10/best-practices-education-hub-creators-instagram/
- Google Search Console (free service): https://support.google.com/webmasters/answer/9128668

## Limits

- X analytics are paywalled without X Premium; Pinterest analytics may be unreachable behind a bot wall; TikTok data needs an active account. Record "unavailable" rather than inventing data.
- No paid SEO tool is assumed. The honest $0 stack is Search Console (measurement) + native search suggestions (discovery) + a chatbot (briefs/outlines) — never present AI-generated keyword volumes as measured data.
- Character limits change. The figures in this skill were verified 23 Nov 2026 (X 280, Threads 500, IG 2,200, Pinterest description 800 API / 500 in-app, LinkedIn 3,000, Facebook 63,206, YouTube description 5,000). Re-check any figure before building a post on it.
