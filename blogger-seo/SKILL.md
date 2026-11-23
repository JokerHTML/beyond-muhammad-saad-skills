---
name: blogger-seo
description: Rank a Blogger blog on Google for $0 — setup, keyword research, on-page and technical SEO, indexing, and a 20-flaw pre-publish gate. No plugins, no paid tools, no coding.
version: 1.1.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
---

# Blogger SEO & Ranking

**Companion skill:** `../blog-writing/SKILL.md` — the Blog Writing skill is the authority for the writing itself (thesis, research, titles, structure, the 22-flaw writing gate, the 100-point rubric). This skill covers the *platform*; the Blog Writing skill covers the *writing*. Cross-references are by section number. Do not merge the two.
**Labelling (used throughout):** **FACT** = officially confirmed (Google Search Central, Blogger Help, or another primary source). **SIGNAL** = corroborated by multiple independent practitioner sources. **SPECULATION** = single-source or opinion — a judgement call, not a rule.
**Re-verification discipline (§15):** Blogger reorganises its settings periodically, and prices on other platforms change without notice. Every menu path in this skill was verified against Nov 2026 guides and Blogger Help pages; the live dashboard is the final authority. If a path has moved, follow the live dashboard, note the change, and re-check the dated items in §15 before teaching them.

## Purpose

Take a Blogger blog from zero to the top of Google search results for its topics — on a $0 budget, with no plugins, on a free `blogspot.com` address or a custom domain. The skill covers one-time setup, keyword research, post-writing SEO, on-page and technical optimisation, a pre-publish gate, indexing, tracking, and the flaw-fix loop. It is written for someone who has never used Blogger.

## When to use

- Setting up a new Blogger blog (or fixing an existing one that does not rank).
- Before writing any post (keyword + intent first).
- Before publishing any post (run the pre-publish gate, §10).
- Weekly: Search Console check, indexing triage, refresh candidates.
- Monthly: flaw sweep, speed check, backlink and content audit.
- When deciding Blogger vs WordPress.com Free vs Medium (§11).

## Rules (hard)

- **Never invent ranking data.** No keyword volume, difficulty score, ranking boost percentage, traffic figure, or time-to-rank promise unless a tool actually measured it. If unmeasured, say "unmeasured — chosen from audience wording" and quote no number.
- **Never sell a ranking hack.** No guaranteed rankings, no "index in 24 hours" service, no secret factor, no GEO/AEO trick. Google guarantees nothing — not crawling, not indexing, not ranking — even for pages that follow every rule (**FACT**, How Search Works).
- **No fake claims, ever.** No invented credentials, awards, "as featured in", traffic numbers, or earnings. Author credibility is built from real experience, named sources, and visible corrections — never fabricated.
- **One primary keyword / one search intent per post.** Secondary phrases only if genuinely relevant (3–8 max). One strong post per intent; never publish near-duplicate posts chasing keyword variants — that is scaled thin content, a named spam policy (**FACT**).
- **Blogger has no plugins.** There is no Yoast/Rank Math equivalent. Everything in this skill is done with Blogger's own settings, the theme editor, and free Google tools. Any guide promising a plugin workflow on Blogger is wrong.
- **Every claim about how Google ranks must trace to an official source or be labelled.** Practitioner folklore (keyword density, "first 100 words", word-count targets, daily-posting mandates) is called out as folklore in §12 — never teach it as fact.
- **Universal rule:** this skill contains no brand-specific content. Topics are neutral; user-specific values go in [bracketed placeholders] (e.g. `[your blog name]`, `[your topic]`, `[your name]`).

## The ranked key points (must-do → nice-to-have)

Read this list first. Everything else in the skill is the how-to for one of these lines.

**Must-do — without these, nothing else matters:**
1. **One query, one complete, genuinely helpful post** with first-hand experience (original photos/screenshots, your own measurements, what you actually tried). Thin content is the #1 killer — Google's helpful-content system targets content made mainly to gain search traffic (**FACT**).
2. **Indexing verified, not assumed:** "Visible to search engines" ON, blog verified in Google Search Console, `sitemap.xml` + `sitemap-pages.xml` submitted, each important post checked with URL Inspection. A page that is not indexed cannot rank at all (**FACT**).
3. **One primary keyword per post**, placed naturally in the title, the custom permalink, the opening answer, and a heading. Never chase a density number — Google publishes none.
4. **Unique title + unique search description per post.** The description is **not** a ranking factor (**FACT**, Google since 2009) — it earns the click. A missing description costs clicks, not rank. Google rewrites descriptions most of the time (Ahrefs 2020: 62.78%; see blog-writing §6.4) — write it anyway; when it shows, it is your snippet.
5. **Custom permalink set BEFORE publishing** — short, lowercase, hyphenated, keyword-first, 3–6 words. Blogger locks the URL to `domain/YYYY/MM/slug.html`; changing a live URL 404s the old one.
6. **Internal links on every post:** ≥2 in-text links to older related posts, and link back to the new post from 1–2 older posts. Keep labels few and consistent (1–3 per post, 5–10 for the whole blog) so label pages are real topic hubs. **Advanced (adopted from the best surveyed guides):** organise posts into pillar + cluster groups — one pillar post per core topic, 6–12 cluster posts linking to it and to each other. Optional; the ≥2-links rule above is the floor.
7. **Leave custom robots.txt and custom robots header tags OFF** unless you have a diagnosed reason. Blogger's default robots.txt already blocks `/search` (label/search pages). A custom file **replaces** the default entirely — omitting its lines silently drops them.
8. **Images done properly:** compress before upload, descriptive filename, alt text (long description, per Blogger Help) + title (short description) via the editor's Edit dialog. Never keyword-stuff alt text.
9. **Light, responsive theme, few gadgets.** Speed work on Blogger is subtraction: remove unused gadgets/scripts, limit fonts, compress images. Measure with PageSpeed Insights (LCP ≤2.5s, INP ≤200ms, CLS ≤0.1 = "good", **FACT**).
10. **Author credibility signals:** About page, author byline on posts, contact route, sources cited. E-E-A-T is **not** itself a direct ranking factor (**FACT**) — but trust is what Google's systems are tuned to reward, and readers click trusted authors.

**Nice-to-have / advanced — do these after the must-dos are solid:**
11. **Custom domain when ready** (~$10–20/yr for a .com, **SIGNAL**) — a branding and portability decision, **not** a ranking hack. Blogspot is not penalised and a custom domain gives no ranking boost. Blogger auto-redirects old blogspot URLs.
12. **BlogPosting JSON-LD — only after inspecting the theme.** Stock themes may already ship Article/BlogPosting markup; never add a second competing object. Validate the live URL in Rich Results Test. Schema cannot force indexing or rankings.
13. **Update top posts honestly:** refresh only with substantial changes, keep the URL, add a visible "Last updated: [date]" line. Never bump a date without a real edit — Google lists that as a search-engine-first warning sign (**FACT**). Changing the Blogger post date changes its URL.
14. **Earn links, never buy them.** Guest posts on real niche blogs, journalist-source platforms, broken-link building, one genuinely linkable asset. Buying links for ranking is a named spam-policy violation (**FACT**); SpamBrain neutralises unnatural links.
15. **Canonical discipline when cross-posting:** publish on Blogger FIRST, then set the canonical on the other platform (Medium Import tool / canonical link) pointing back to the Blogger URL. Canonical is a hint, not a directive — Google may still pick the other copy.
16. **Back up regularly** (Settings → Manage blog → Back up content; Google Takeout). Google controls the platform and can remove a blog for policy violations — never keep the only copy of anything on Blogger.
17. **Track in Search Console weekly; fix with content, not requests.** "Crawled – currently not indexed" after ~2 weeks means improve the content. Do not re-request indexing repeatedly.

## 1. One-time setup checklist

Do these once, in order, before the first post. Every item is free. Menu paths verified against Nov 2026 guides (see §15); the live dashboard is the final authority.

- [ ] **Create the blog** at blogger.com with the Google account that will own it. Blog title = [your blog name]; address = `[your-topic].blogspot.com` (short, memorable, no keyword stuffing).
- [ ] **Settings → Privacy → "Visible to search engines" ON** and blog set to Public. (If this is OFF, nothing ranks. Whether it defaults ON for new blogs is **unverified** — check it, do not assume it.)
- [ ] **Settings → Meta tags → "Enable search description" ON**, then write a ~150-character blog summary (keyword + what the blog is about). This toggle may be a prerequisite for per-post descriptions (**unverified** — verify on the live dashboard).
- [ ] **Settings → Basic → HTTPS → HTTPS Redirect ON.** Blogspot is always HTTPS (**FACT**); the redirect makes sure visitors always reach the encrypted version.
- [ ] **Theme → pick a modern responsive theme** (Contempo, Soho, Emporio, Essential, Notable). **Back up the theme first** (Theme → ⋮ → Backup → Download) before any edit. Set Mobile settings to show the desktop (responsive) theme, not a legacy mobile theme.
- [ ] **Theme → Layout → remove every gadget that does not serve a reader goal** (counters, clocks, weather, chat boxes, duplicate widgets). Keep: search, labels/navigation, about.
- [ ] **Labels plan:** decide 5–10 topic labels for the whole blog before writing. Write them down. Never invent a new label per post.
- [ ] **Pages → create About + Contact pages.** About: who you are, what you have actually done in [your topic], with a photo. Contact: a form or an email address. Add both to the nav (Layout → Pages gadget).
- [ ] **Settings → Basic → Google Analytics Measurement ID:** paste the GA4 `G-` ID (free; create the property at analytics.google.com first). Note: Blogger's settings text says this field is "specific to dynamic views and layout themes" — verify it works on your theme; on a classic theme you may need to paste the tag manually. GA4 data is **not** used in rankings (**FACT**) — it is for your decisions only.
- [ ] **Google Search Console:** search.google.com/search-console → Add property → **URL-prefix** with the exact blog address → verify by HTML tag (paste the meta tag into Theme → Edit HTML, before `</head>`), or via the GA4 connection on the same account. Then **Indexing → Sitemaps → submit `sitemap.xml`**, then **`sitemap-pages.xml`**. Blogger auto-generates both (**FACT**). Over 500 posts, also submit the `?page=N` variants — sources disagree on whether this is needed (see §14); submitting them is harmless.
- [ ] **Link GA4 ↔ Search Console** (GA Admin → Product links → Search Console) for combined reporting.
- [ ] **Settings → Posts → lazy-load images ON and WebP serving ON** where those options appear. Do not lazy-load the hero/LCP image (see §4).
- [ ] **Settings → Errors and redirects → Custom 404:** add a helpful not-found page that links to your main topics. **Custom redirects:** set a permanent (301) redirect whenever a live URL changes or a post is deleted — never leave a dead URL.
- [ ] **Leave OFF (do not touch):** custom robots.txt, custom robots header tags. Defaults are appropriate for most blogs (**SIGNAL**). Only touch them for a diagnosed reason (§4).
- [ ] **Custom domain (optional, later):** Settings → Publishing → Custom domain. Must be `www.` or a subdomain — Blogger does not serve naked domains (**FACT**). DNS: CNAME `www` → `ghs.google.com` + the verification CNAME Blogger shows; enable Redirect domain (root → www) and HTTPS Availability, wait ~15–60 min for the certificate (**SIGNAL**), then HTTPS Redirect ON. Verify old blogspot URLs redirect (check 5–6 posts), re-register the new domain in Search Console, submit its sitemap. Do not change theme or post URLs on the same day as the domain move.

## 2. Keyword research — the $0 stack

1. **Search Console → Performance** (after the blog has any impressions): the actual queries your pages already appear for, with clicks, impressions, CTR, position. Only works after verification; no backfill before it.
2. **Google autocomplete + People Also Ask + Related Searches:** real phrasing of what people type. Use a private window (results are personalised). No volume — that is fine.
3. **Google Trends:** relative interest over time (0–100 scale), seasonality, rising queries. Relative only, never absolute volume.
4. **Google Keyword Planner:** estimated monthly volume **ranges** (e.g. 100–1,000) from Google's own data. Lives inside Google Ads; whether billing information is required with no ad spend is **unverified** (sources disagree).
5. **Read the top 10 results yourself** for the query: who ranks, how thorough they are, whether a new blog could plausibly beat them. No free Google tool gives a difficulty score — this reading *is* the difficulty check.

**Pick one primary phrase per post** — the variant with the clearest intent match + most native evidence — and 3–8 secondaries. Intent types: learn / compare / do / buy / troubleshoot. One post = one intent. If two phrases mean the same thing to the searcher, they are one post, not two.

**Do not teach or use:** keyword density percentages, "keyword in the first 100 words", LSI keywords, word-count targets. Google publishes none of these; keyword stuffing is a spam-policy violation (**FACT**).

**Per-post keyword output (paste into every post brief):** primary search phrase + reader intent · 3–8 secondary phrases · title (primary phrase near the front, ~50–60 chars) · custom permalink (short, hyphenated, keyword-first) · search description (~140–160 chars, keyword + benefit first) · H2 outline (each heading describes its section) · alt text plan (one line per image) · internal links planned (≥2 older posts + which older post will link back) · labels (1–3 from the blog's fixed set).

## 3. Post-writing SEO — the process

The writing itself — thesis, claim sheet, outline, draft, edit, the 22-flaw writing gate — is the Blog Writing skill's job (blog-writing §1–§9). This section is only the platform mechanics that sit on top of it:

1. **Start from the audience problem, not a keyword tool.** Write the question a beginner would type, in their words. Check what the top 10 results actually answer — then answer it better, with something they do not have (your own test, screenshots, data, a mistake you made).
2. **Draft the post around one query.** Direct answer in the first paragraphs, then depth: steps, examples, screenshots from your own experience, named sources. No minimum word count — completeness for the query is the test (**FACT**: Google has no preferred word count).
3. **Structure:** post title = the only H1 (Blogger does this automatically on most themes — **verify per theme** by viewing page source; older/default templates may put the blog name as H1 and the post title as H3 — if so, fix in the theme or pick a theme that already does it right). **Live finding (23 Nov 2026, verified on a real default-template blog): the post title renders as `<h3 class="post-title">` and the page contains NO `<h1>` element at all.** The H1 warning is real, not theoretical — check your own theme's page source before you assume the title is the H1. Body: H2 for main sections, H3 for sub-points, in reading order. Headings describe their section; they are a navigation aid, not a keyword trick — Google says heading number/order "doesn't matter from a Google Search perspective" (**FACT**).
4. **Title:** unique, descriptive, primary phrase near the front, ~50–60 characters as a display guideline (not a Google rule — Google truncates to device width and rewrites titles that are missing, repeated, stuffed, or undescriptive; Zyppy 2022: 61.6% rewritten; McAlpin Q1 2025: 76.0% — see blog-writing §4.2). No clickbait: the title is a promise the page must keep.
5. **Permalink:** Post settings → Permalink → Custom Permalink → short, lowercase, hyphenated, keyword-first, 3–6 words, no stop words, no year (the date is already in the path). Set **before first publish**.
6. **Search description:** Post settings → Search description → one unique ~140–160-character summary per post: keyword + benefit first. Expect Google to rewrite it often; it shapes the snippet/CTR, not rank.
7. **Images:** compress/resize before upload (aim <100 KB standard, <50 KB thumbnails — practitioner target, not a Google rule). Descriptive filename before upload (`[topic]-example.jpg`, not `IMG_0083.jpg`). In the editor, click the image → Edit → alt = long description, title = short description (**FACT**, Blogger Help wording — several guides invert this; follow the official wording). Describe the image; never keyword-stuff. Decorative images: empty alt.
8. **Internal links:** ≥2 in-text links to older related posts, with descriptive anchor text that makes sense on its own (never "click here"). After publishing, edit 1–2 older related posts to link to the new one. Add 1–3 labels from your fixed label set.
9. **External links:** link out to reliable sources for verifiable claims. That is a trust signal, not a leak.
10. **Author byline:** end every post with 1–2 lines — name, one real credential/experience, link to About.

## 4. Technical setup (beyond §1)

- **Robots.txt:** leave the default alone. Default blocks `/search` and `/share-widget` and declares the sitemap — **verified live 23 Nov 2026** by fetching a default-template blog’s robots.txt (HTTP 200; `Disallow: /search`, `Disallow: /share-widget`, `Sitemap:` line present). A custom file replaces it entirely — if you ever need one, copy the default verbatim first, then add only the diagnosed rule, and always keep the `Sitemap:` line. Robots.txt controls crawling, **not** indexing/removal — use `noindex` for removal.
- **Robots header tags:** leave OFF. If ever enabled: `all` for Home and Posts/Pages, `noindex` (+ `follow`, the safer of the two disputed options) for Archive/Search. Never `noindex` Posts/Pages. `noodp` is legacy (the Open Directory Project closed in 2017) — do not teach it as a live control.
- **Labels and label pages:** label pages live under `/search/`, which the default robots.txt already disallows — so they are crawl-blocked by default. That is normal, not an error. Only consider indexing label pages once a label has ≥5 substantial posts AND you add a custom robots.txt allowing `/search/label/` — an advanced step. Never combine robots-allow with header-noindex on the same pages. The per-blog label cap is **unverified** (2,000 vs 5,000 in conflicting sources); the agreed limit is 20 per post.
- **Structured data:** inspect the rendered HTML of a live post first — stock themes may already ship Article/BlogPosting JSON-LD. **Live finding (23 Nov 2026, verified on a real default-template blog post): the stock template DOES ship a `BlogPosting` JSON-LD block (with headline) — so on a default theme, do NOT add a second one.** If none exists, add one BlogPosting block in the theme (Theme → Edit HTML, inside the post includable, gated by `<b:if cond='data:view.isPost'>`, using Blogger data tags like `<data:post.title/>` so fields populate per post). Validate the live URL in Rich Results Test. Do not duplicate an existing object. Do not build a strategy on FAQ schema (its rich result is reported deprecated — single source, **unverified**).
- **Speed:** measure first (PageSpeed Insights — homepage + a typical post + a label page, mobile). Fix LCP/CLS first. Blogger has a **Lazy load images** setting — do not lazy-load the hero/LCP image. No caching plugin, no server config, no CDN control exists on Blogger. A PageSpeed score of 100 is not required for ranking.
- **Mobile:** Google is mobile-first since Oct 2023 — it primarily uses the mobile version for indexing and ranking (**FACT**). Content that only appears on desktop is effectively invisible. Test on a real phone: text readable without zooming, links tappable, no horizontal scrolling, images scaled. Keep mobile and desktop content identical.
- **HTTPS:** blogspot is always HTTPS; custom domain needs HTTPS Availability + Redirect (see §1).

## 5. Indexing — getting posts found

- Google guarantees nothing: "doesn't guarantee that it will crawl, index, or serve your page" (**FACT**). Expect days to weeks for a brand-new blog, hours to days once established — timelines conflict across sources, so treat them as ranges, not promises.
- **Per new post:** (1) publish, (2) Search Console → URL Inspection → paste URL → **Request Indexing once**. Do not repeat the request. (3) Link to it from 2–3 already-indexed pages — discovery via links is Google's primary mechanism (**FACT**).
- **If a post is not indexed:** read the exact GSC status first. "Discovered – currently not indexed" = known, not yet crawled (wait). "Crawled – currently not indexed" = crawled, judged not worth indexing — usually a quality/thin/duplicate judgement; **fix the content**. "Duplicate without user-selected canonical" = check the canonical. Do not delete and republish the same post repeatedly; do not resubmit the sitemap repeatedly.
- **The `?m=1` mobile-URL theory** (that Blogger's mobile URL variant causes indexing errors) is single-source and **unverified** — do not treat it as a diagnosis without Search Console evidence.
- **"Blogger gets indexed faster because Google owns it" is SPECULATION.** No Google document promises it, and practitioner timelines (weeks for a new blog) contradict it. Blogger's only advantage is that the technical setup (HTTPS, sitemap, mobile) is already correct.

## 6. Updating old posts (freshness, done honestly)

- Freshness matters only where the query expects it (news > definitions) — "query deserves freshness" (**FACT**). There is no Google statement that an old page loses rank merely for being old.
- **Refresh candidates:** posts ranking ~positions 6–20 in Search Console, or with slipping clicks. Substantial rewrite only: correct facts, add new sections, answer new questions, fix broken links, improve images.
- **How:** keep the URL and slug unchanged. Add a visible "Last updated: [date]" line and say what changed. Only change the visible date if the update was substantial. **Never** change the Blogger post date just to look fresh — that changes the URL (year/month are in the path) and Google lists date-bumping without real changes as a search-engine-first warning sign (**FACT**). If you must change the date, add a permanent Custom Redirect (Settings → Errors and redirects) from the old URL to the new one, and request indexing once.
- **Quarterly:** open the top 10 posts by GSC clicks, fix stale facts and dead links, add 1–2 new internal links. Refreshing on the same URL preserves ranking history; republishing as a new post starts from zero.

## 7. Backlinks — the $0 safe list

- PageRank remains a core ranking system (**FACT**, Ranking Systems guide). Domain Authority / Domain Rating are **not** Google metrics — never quote them as Google signals.
- **What works:** complete profiles on the platforms your audience actually uses (blog URL in profile — mostly nofollow; value is discovery and credibility); reputable niche-relevant directories only; editorial guest posts on real small-to-medium blogs in the same niche; journalist-source platforms (answer queries with specific expertise — platform names change; verify the current name before teaching one); broken-link building; one genuinely linkable asset (original data, a free checklist/tool, a thorough original guide). Genuine community participation (Reddit, niche forums, Quora) where a link is a helpful answer — typically nofollow and moderated.
- **What to avoid (spam policies, FACT):** buying/selling links for ranking, excessive link exchanges, automated link creation, low-quality directory/bookmark blasts, keyword-rich hidden links in widgets, advertorials with links passing ranking credit. Paid links are acceptable only if qualified `rel="nofollow"` or `rel="sponsored"`. SpamBrain **neutralises** unnatural links (credit lost, not usually a penalty); a manual action is still possible for serious violations.
- **Disavow** only if you have many spammy links **and** they caused (or likely will cause) a manual action. A new blog should never disavow pre-emptively.
- No free method reliably produces links in days. Expect weeks to months.

## 8. Cross-posting & canonical discipline

- **Publish on Blogger FIRST.** Then syndicate elsewhere with the canonical pointing back: Medium Import tool (sets it automatically) or Story Settings → Advanced → "Customize canonical link" → paste the Blogger URL. Dev.to: `canonical_url` in front matter.
- **Canonical is a hint, not a directive** (**FACT**) — Google may pick the Medium copy anyway, especially on a stronger domain. That is dilution, not a "duplicate content penalty" (Google: duplicate content is not a spam-policy violation and causes no manual action).
- **Detect:** search an exact sentence from the post in quotes — if the other copy outranks your Blogger post, fix the canonicals and link from the copies back to the Blogger original.
- **Never** publish the same post on Blogger + Medium + elsewhere with no canonical handling, and never publish AI-generated writing behind Medium's paywall (Medium's AI policy forbids paywalling AI-generated writing — **FACT**, Medium Help, updated 2026-11-11).

## 9. Tracking & the flaw-fix loop

**Weekly (30 min):**
- Search Console → Performance: queries, clicks, impressions, CTR, average position. Note any page with high impressions + low CTR (title/snippet mismatch — rewrite the title/description).
- Search Console → Indexing → Pages: new "Crawled – currently not indexed" or errors? Fix content first (see §5).
- Search Console → Links → Internal links: any post with 0 internal links is an orphan — link to it.
- One refresh candidate (positions ~6–20) if a substantial update is possible.

**Monthly (1 hour):**
- Run the full pre-publish gate (§10) against the 3 weakest posts; fix what fails.
- PageSpeed Insights on homepage + one post + one label page (mobile). Fix the worst LCP/CLS issue.
- Broken-link sweep on the top 10 posts (GSC Pages → 404s, or click through manually). Fix or remove.
- Labels audit: any label with 1–2 posts, or any post with 4+ labels — merge/fix.
- Backups: download the blog backup (Settings → Manage blog → Back up content) and the theme backup.

**Quarterly:** content audit — merge cannibalising posts (2+ URLs getting impressions for the same query: pick one winner, merge the best parts, redirect the losers), delete or noindex posts that add nothing, refresh the top 10.

**Reality check:** if ~10 genuinely improved posts still earn ~zero outside upvotes/links over months, the bottleneck is usually distribution or topic choice, not another on-page tweak — rethink the topic, not the checklist. Never keep grinding the same pattern indefinitely.

## 10. Pre-publish gate — 20 flaws

Every post must pass this gate before publishing. **A CRITICAL failure = do not publish until fixed.** HIGH = fix now unless you record a dated reason not to. MEDIUM = fix before the next post goes out. Frequency ratings are judgement, not measured statistics — no crawl study of Blogger blogs exists. Run the Blog Writing skill's 22-flaw writing gate (blog-writing §9) too; the two gates are complementary, not alternatives.

### CRITICAL — do not publish with any of these failing

| # | Flaw | Check / fix |
|---|---|---|
| 1 | Thin content / no clear search intent | Post answers ONE specific query completely, with original value beyond the top results. No minimum word count — completeness is the test (**FACT**: Google has no preferred word count). Detect: would a reader bookmark it, or go back to search for a better answer? |
| 2 | Indexing blocked | Settings → Privacy → "Visible to search engines" ON. No stray `noindex` on the post (Post settings → Custom robots tags) and no `noindex` on Posts/Pages in Settings → Crawlers and indexing. A page that is not indexed cannot rank (**FACT**) |
| 3 | Keyword stuffing / clickbait title | Keyword appears naturally (title, intro, a heading) — never repeated awkwardly. Title = the specific promise the page keeps. Keyword stuffing is a named spam policy (**FACT**). Detect: read aloud — if a phrase repeats awkwardly, it is stuffed |
| 4 | Link spam | No bought links, no link exchanges at scale, no automated link building, no paid guest-post links without `rel="sponsored"`/`nofollow`. Violators "may rank lower in results or not appear in results at all" (**FACT**) |

### HIGH — fix now

| # | Flaw | Check / fix |
|---|---|---|
| 5 | Duplicate content without canonical | If this post (or a near-copy) exists elsewhere, the canonical points at the Blogger URL. Canonical is a hint, not a directive (**FACT**) |
| 6 | Defaults not set | Settings → Meta tags → "Enable search description" ON. Both custom-robots toggles OFF unless you have a specific, understood reason. Meta description is **not** a ranking factor (**FACT**, since 2009) — a missing one is a CTR flaw, not a ranking flaw |
| 7 | Sitemap not submitted / Search Console not connected | GSC → Sitemaps shows `sitemap.xml` and `sitemap-pages.xml` (Blogger auto-generates both). A sitemap helps discovery but never guarantees indexing (**FACT**) |
| 8 | Custom permalink not set | Post settings → Permalink → Custom Permalink: short, lowercase, hyphenated, keyword-first, 3–6 words, no stop words. Set **before** first publish. Changing a live URL 404s the old one (fix: revert to draft + permanent Custom Redirect) |
| 9 | No internal links | ≥2 in-text links to older related posts (descriptive anchors, never "click here"), and the post is linked from at least one older post or label hub. Orphans get crawled late or not at all (**SIGNAL**) |
| 10 | Label misuse | 1–3 labels from the blog's fixed 5–10 label set; no label used on only one post; no post with 4+ labels. Label pages live under `/search/`, which the default robots.txt already blocks — normal, not an error |
| 11 | Theme heavy / slow | Layout → unused gadgets removed. Images compressed before upload (<100 KB standard, <50 KB thumbnails — practitioner target). No dead third-party scripts. PageSpeed Insights: LCP ≤2.5s, INP ≤200ms, CLS ≤0.1 = "good" (**FACT**) |
| 12 | Mobile ignored | Responsive theme; on a real phone: text readable without zooming, links tappable, no horizontal scrolling, images scaled. Google is mobile-first since Oct 2023 (**FACT**) |
| 13 | Duplicate title | No other post shares this title; title is not just the blog name; key words early. Google rewrites repeated/stuffed titles (**FACT**) |
| 14 | Stale repost | Facts, prices, screenshots, links are current. A refresh is substantial, the URL is unchanged, and a visible "Last updated: [date]" line says what changed. Never bump a date with no real edit (**FACT**) |

### MEDIUM — fix before the next post

| # | Flaw | Check / fix |
|---|---|---|
| 15 | Missing alt text | Click image → Edit → alt = long description, title = short description (Blogger Help wording). Descriptive filename before upload. Decorative images: empty alt. Never keyword-stuff alt text (worse than none) |
| 16 | No author credibility | Author byline on the post (name + one real credential + link to About). About + Contact pages exist and are in the nav. E-E-A-T is **not** a direct ranking factor (**FACT**) |
| 17 | Cannibalisation | No other post on the blog targets this same query. Check: GSC Performance filtered by the query shows only this URL getting impressions. If two posts chase one query, merge them and redirect the loser |
| 18 | Broken links | All internal and outbound links work. Fix or remove dead ones; after a batch of fixes, request re-indexing of affected URLs once |
| 19 | Comment spam uncontrolled | Settings → Comments → moderation ON (hold for review). Delete spam; never approve a link-drop. User-generated spam is a named Google spam policy (**FACT**) |
| 20 | Intrusive ads / pop-ups | No full-screen interstitial on entry; ads below the first content or in the sidebar; no pop-up gadget covering content. Interstitials covering main content can rank a page lower (**FACT**) |

### Non-flaws — do NOT fail a post for these

Missing meta **keywords** tag (Google has ignored it since 2009, **FACT**) · missing meta description treated as a *ranking* failure (CTR issue only) · no Google Analytics connected (GA data is **not** used in rankings, **FACT**) · Blogspot subdomain instead of custom domain (no Google doc penalises blogspot.com) · not posting daily (no Google doc sets a posting frequency) · post under 1,000 words (Google has no preferred word count, **FACT**).

## 11. Platform decision — Blogger vs WordPress.com Free vs Medium

Prices/limits are dated snapshots — re-check the official page on the day of use (§15).

> **Pick Blogger** if the goal is Google search traffic on a $0 budget AND you want to own the address and the ad revenue: free blogspot start, attach a custom domain later (~$10–15/yr) with no platform fee, full Search Console access, AdSense from day one (subject to quality review — Google publishes **no** minimum post count, traffic floor, or domain-age rule; those numbers in guides are folklore). Accept weaker SEO tooling (no plugins, manual schema) and a clunky export path — mitigate by backing up via Takeout regularly and moving to a custom domain early so the domain, not blogspot, holds the equity.
>
> **Pick WordPress.com Free** if the goal is learning the WordPress editor/ecosystem with a clean upgrade path to self-hosted WordPress.org later, and you accept $0 revenue and no SEO controls (no meta descriptions until Premium $8/mo billed annually, renews $9/mo; no custom domain, WordPress.com ads shown) until you pay. It is a stepping stone, not a destination.
>
> **Pick Medium** if the goal is readers *now* with zero setup, and search ownership is secondary: built-in distribution, fast indexing on a strong domain, and (with a $5/mo membership, $50/yr) Partner Program earnings from member reading time. Partner Program bar (per Nov 2026 reads of Medium Help — re-check the eligibility page on the day of use): ≥6 published stories, 3+ months active, complete profile, bank + tax residence in an eligible country, age 18+; minimum payout $10 via Stripe. Note: some Nov 2026 guides dispute whether the paid membership itself is required to apply — treat Medium's own eligibility page as the source of truth. Use it as a distribution/repurposing channel, never as the canonical home of cornerstone content.

Key comparison facts: Blogger — $0 forever, no forced ads, custom domain free (domain purchase only), per-post search descriptions, full Search Console, AdSense eligible on a free blogspot address (original high-quality content, policy compliance, access to site HTML, age 18+; payout threshold $100 for USD accounts, **SIGNAL** — verify in AdSense Help before quoting). WordPress.com Free — 1 GB storage, WordPress.com ads shown, no plugins, no custom domain, SEO controls from Premium ($8/mo billed annually, renews $9/mo — Nov 2026 reads). Medium — publishing $0, earning needs $5/mo membership ($50/yr), ≥6 published stories + 3+ months active, complete profile, bank + tax residence in an eligible country (check Medium's current eligible-country list — do not quote a country from memory), age 18+; minimum payout $10 via Stripe; AI-generated writing cannot be paywalled. Export: Blogger via Google Takeout (`feed.atom`) + theme backup separately — note: WordPress's built-in Blogger Importer was written for the old XML export and does not read the new Takeout `feed.atom` (broken since July 2025, **SIGNAL**); third-party importers are the workaround. **Practical combination:** Blogger as home base; Medium as distribution — syndicate to Medium with a canonical link back to Blogger once the Blogger post exists.

## 12. Myths to ignore

This table and the Blog Writing skill's §11 myths table were cross-checked on 2026-11-23 and agree on every overlapping row. Where they overlap, the wording below is the harmonised version.

| Myth | Google's position |
|---|---|
| Meta keywords tag helps ranking | "Google Search doesn't use the keywords meta tag" — ignored since 2009 (**FACT**) |
| Keyword density ~2% / LSI keywords | No target density anywhere in Google docs; stuffing = spam policy; Google says it does not use LSI (**FACT**) |
| Meta description is a ranking factor | "We still don't use the description meta tag in our ranking" — CTR/snippets only (**FACT**) |
| E-E-A-T is a direct ranking factor | "No, it's not" — it is the quality-rater framework, not a factor (**FACT**) |
| Word-count targets (1,500–2,000+, pillar 2,500–4,000) | "The length of the content alone doesn't matter… no magical word count target" (**FACT**) |
| Posting daily / at a set frequency ranks better | "Posting daily or at any specific frequency… doesn't help with ranking better" (**FACT**) |
| Blogspot.com can't rank / Google favours its own platform | No Google document penalises blogspot; no Blogger bonus exists. Google evaluates pages, not platforms (**SIGNAL**) |
| "Duplicate content penalty" for label/archive pages | "Having duplicate content on your site is not a violation… not something that will cause a manual action" (**FACT**) |
| Sitemap / indexing service guarantees indexing | A sitemap helps discovery; listing a URL "doesn't guarantee it will be crawled or indexed" (**FACT**) |
| Custom robots.txt improves rankings | Robots.txt controls crawling; "it is not a ranking boost" (**FACT**) |
| Heading count/order is a ranking lever | "From Google Search perspective, it doesn't matter if you're using [headings] out of order… no magical, ideal amount" (**FACT**) |
| GA data / bounce rate / dwell time are ranking factors | Google: "We don't use that at all" for GA data; dwell time/CTR denied as factors. Click/interaction data exists in some form (NavBoost, sworn testimony 2023; API leak 2024) but no per-page threshold or target exists — optimise for the reader, never game the metric |
| "Keyword in the first 100 words" rule | No Google source — practitioner folklore (**SPECULATION**) |
| DA/DR scores are Google signals | Third-party metrics, not Google's (**FACT**) |
| Exact-match / keyword-rich domain = SEO advantage | "Keywords in the domain… alone have hardly any effect beyond appearing in breadcrumbs" (**FACT**) |
| Time-to-rank "3–6 months" | Practitioner rule of thumb; Google only says timing varies from hours to months (**SPECULATION**) |
| "Blogger indexes faster because Google owns it" | No Google document promises it (**SPECULATION**) |

## 13. Official references

- Google Search Central — SEO Starter Guide (updated 10 Dec 2025): https://developers.google.com/search/docs/fundamentals/seo-starter-guide
- Google Search Central — Creating helpful, reliable, people-first content: https://developers.google.com/search/docs/fundamentals/creating-helpful-content
- Google Search Central — How Search Works: https://developers.google.com/search/docs/fundamentals/how-search-works
- Google Search Central — Ranking Systems Guide: https://developers.google.com/search/docs/appearance/ranking-systems-guide
- Google Search Central — Spam policies: https://developers.google.com/search/docs/essentials/spam-policies
- Google Search Central — Understanding page experience: https://developers.google.com/search/docs/appearance/page-experience
- Google Search Central — AI features and your website (last updated 2025-12-10): no additional requirements for AI Overviews / AI Mode
- Blogger Help — Manage your blog's settings: https://support.google.com/blogger/answer/9691230
- Blogger Help — Help people find your blog on search engines: https://support.google.com/blogger/answer/2523525
- Blogger Help — Turn on HTTPS: https://support.google.com/blogger/answer/6284029
- Blogger Help — Custom domain: https://support.google.com/blogger/answer/1233387
- Blogger Help — Back up / import content: https://support.google.com/blogger/answer/41387
- Medium — AI content policy (updated 2026-11-11): https://help.medium.com/hc/en-us/articles/22576852947223-Artificial-Intelligence-AI-content-policy
- Google Search Console (free): https://search.google.com/search-console
- Google Analytics 4 (free): https://analytics.google.com
- Google Trends (free): https://trends.google.com
- PageSpeed Insights (free): https://pagespeed.web.dev
- Rich Results Test (free): https://search.google.com/test/rich-results

## 14. Limits — what this skill does NOT cover, and what is unverified

- **No paid tools.** The honest $0 stack is Search Console + GA4 + Trends + autocomplete/People Also Ask + Keyword Planner ranges. Never present AI-generated keyword volumes as measured data.
- **No live-dashboard verification was done while building this skill.** Blogger reorganises settings periodically; menu paths in this skill were verified against Nov 2026 guides and Blogger Help pages, but the live dashboard is the final authority. If a menu path has moved, follow the live dashboard and note the change (§15). **What HAS been verified live (23 Nov 2026, Round 2):** the default robots.txt (live fetch), both sitemaps (`sitemap.xml` + `sitemap-pages.xml`, both HTTP 200), the stock template's BlogPosting JSON-LD, and the post-title heading level (H3, no H1) — all on a real live blogspot blog. A signed-in dashboard walk of §1 is still owed.
- **Unverified items — do not teach as fact (verify with the stated method first):** Blogger storage limit (sources conflict — quote no number; check the live Blogger Help storage article from a signed-in account); label cap (2,000 vs 5,000; agreed limit is 20 per post); whether the blog-level "Enable search description" toggle is a prerequisite for per-post descriptions (toggle it off on a test blog and check page source); whether "Visible to search engines" defaults ON for a new blog (create a fresh test blog and read the default); `?m=1` mobile-URL indexing harm (single source — needs Search Console evidence); sitemap pagination (150 vs 500 URLs per file; inspect a large Blogger blog's sitemap.xml); indexing timelines (ranges only, never promises); Search Console Request-Indexing daily limit (exact number not verified); Keyword Planner billing requirement (sources disagree — test with a fresh Google Ads account); whether noindexing label pages helps (practitioner advice only); any ranking weight or percentage for any factor (Google publishes none); WordPress.com Free plan details and Medium regional pricing (re-check the official pricing pages on the day of use); migration traffic-loss figures (20–40%, 60–90 days — single anecdotal source); "60% of searches are mobile" (no Google figure — do not use it); HubSpot refresh statistics ("106% lift" — single-source vendor data, several years old).
- **Verified live 23 Nov 2026 (previously unverified — now closed, see §15):** default robots.txt contents (live fetch of a default-template blog’s robots.txt: blocks `/search` + `/share-widget`, declares sitemap — matches §4); stock-theme BlogPosting JSON-LD (present on a live default-template post, with headline — do not add a second object); post-title heading level (the same live post's title renders as H3 and the page has NO H1 at all — see §3.3). These three were verified on one default template; other themes (Contempo, Soho, Emporio, Essential, Notable) still need their own view-source check before you teach them as universal.
- **YouTube companion gap (still open):** no current, top-cited YouTube Blogger SEO tutorial was verified in the research pass — the video courses found (Class Central listings) are older/undated multi-part courses, and one 2026 guide embeds a single beginner video. A video companion is a gap, not a finding of absence; do not cite a YouTube tutorial as a source until one has been watched and its claims checked.
- **Time-to-rank:** Google only says hours to months. Never promise a date.

## 15. Re-verification discipline — how this skill stays true

Blogger reorganises settings; Google updates its docs; other platforms change prices. This section is the maintenance contract — without it, the skill rots.

| Item | Last verified | Re-check method | Re-check by |
|---|---|---|---|
| All §1 menu paths (Privacy, Meta tags, HTTPS, Crawlers and indexing, Errors and redirects, Posts) | Nov 2026, against two independent 2026 guides + Blogger Help | Open a live Blogger dashboard; walk §1 in order; note any moved/renamed item | Every 6 months, or before teaching the skill to someone new |
| Default robots.txt contents (`/search`, `/share-widget`, sitemap lines) | **Verified live 23 Nov 2026** — fetched a default-template blog’s robots.txt: blocks `/search` + `/share-widget`, declares `sitemap.xml`. Matches §4 | Re-fetch on any new blog before teaching | Every 6 months |
| Post-title heading level (H1 vs H3) + stock-theme BlogPosting JSON-LD | **Verified live 23 Nov 2026** — a default-template blog post: title renders as H3, NO H1 on the page; `BlogPosting` JSON-LD present with headline. Default template only — other themes still need their own view-source check | View source of a live post per theme (Contempo, Soho, Emporio, Essential, Notable) | Before teaching a new theme |
| Google Search Central docs (§13) | Nov–Dec 2025 updates noted in §13 | Re-open each linked doc; record its "last updated" date | Every 6 months |
| WordPress.com Free / Premium prices (§11) | Oct–Nov 2026, secondary reads only | Open wordpress.com/pricing live | On the day of use |
| Medium membership ($5/mo) + Partner Program rules (§11) | Nov 2026 (policy updated 2026-11-11) | Open medium.com/membership + Medium Help AI policy | On the day of use |
| AdSense $100 payout threshold | Secondary sources only | Open support.google.com/adsense/answer/1709871 | Before quoting it |
| Keyword Planner billing requirement | Unverified, sources disagree | Fresh Google Ads account → "Get ideas for new keywords" with no ad spend | Before teaching it |

**Rule:** a dated item that has not been re-checked by its date is taught as "last verified [date] — re-check before relying on it", never as a current fact. When a re-check changes a path, price, or rule, update this table and the section that cites it in the same edit — a skill with a stale §15 and a fresh §1 is worse than a skill that admits it is dated.

## Changelog (publish history)

- **v1.1.0 — 2026-11-23 (Round 2):** Renamed `blogger-seo-ranking` → `blogger-seo` (shorter; "Blogger SEO" is the standard search phrase and how the companion text already refers to it); frontmatter description rewritten as a hook. **Three unverified items closed by live checks on a real Blogspot blog (23 Nov 2026):** default robots.txt fetched (blocks `/search` + `/share-widget`, declares sitemap — matches §4); stock template DOES ship `BlogPosting` JSON-LD (do not add a second object); post title renders as H3 with NO H1 on the page (the §3.3 warning is real — check your theme's page source). Both sitemaps verified HTTP 200. **CORRECTED §11:** Medium Partner Program bar is ≥6 published stories + 3+ months active, not "≥1 published story" (re-verified Nov 2026; membership-required-to-apply is disputed — Medium's own eligibility page is the authority); WordPress.com Premium renewal noted ($8/mo billed annually, renews $9/mo). Companion cross-references in blog-writing updated to the new folder name. See UPGRADE-NOTES.md (Round 2) and TEST-LOG.md (Round 2 live-verification run).
- **v1.0.0 — 2026-11-23:** Publishable universal version. Source was already universal by design; changes: added §15 re-verification discipline (menu paths, prices, docs — each with method and date); added Custom 404 + Custom redirects and lazy-load/WebP settings to the §1 checklist (adopted from the best surveyed 2026 guides); added the pillar + cluster internal-linking option to key point 6 (adopted from the best surveyed guides); cross-checked the §12 myths table against the Blog Writing skill's §11 table — all overlapping rows now agree (meta description, E-E-A-T, word count, AI content, duplicate content, freshness, custom domain, Blogspot); replaced the region-specific Medium example with "check the current eligible-country list"; recorded the open YouTube-companion gap in §14. No claims were removed for inaccuracy; the dated stats the skill relies on (Zyppy, Ahrefs, McAlpin) were re-verified on 2026-11-23 — see UPGRADE-NOTES.md.
