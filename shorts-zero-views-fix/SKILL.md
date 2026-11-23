---
name: shorts-zero-views-fix
description: Diagnose why a YouTube Short is stuck at 0 views and fix it legally — a 10-cause ladder, the Oct 1 2026 originality update, and realistic expectations from named studies, every claim tied to a source. For Shorts creators, not guesswork.
version: 1.1.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
updated: 2026-11-23
---

# Shorts Zero-Views Fix — Diagnose Why a Short Gets 0 Views and Fix It Legally

## Purpose

A Short at 0 views after ~24 hours was **not served, is blocked, or is not a Short** — it is a distribution problem, not a retention problem. This skill finds which one, in order, and fixes it without breaking YouTube's rules.

## When to Use

- A public Short is at 0 (or 0–5) views after 24 hours.
- A channel's Shorts all stall at the same low level.
- Before uploading a Short built from someone else's footage.
- Before concluding a channel is "shadowbanned" or "bugged" — check this ladder first.

## Evidence Labels

- **FACT** — read on an official YouTube/Google Help page. Answer ID named.
- **SIGNAL** — credible secondary source: a large-sample study or trade press, with date, sample, and caveats. Observational, not an experiment.
- **SPECULATION** — creator folklore with no published source. Flagged, never acted on as fact.
- **CONFLICTING** — YouTube's own pages disagree. Treat as a risk, not a rule.

## 1. The One Rule That Reframes Everything

**Since 31 Mar 2025 (Shorts) / 24 Aug 2026 (all formats), a view counts the moment playback starts.** A 1–2 second swipe counts. So a Short at **0 after ~24h was not served, is blocked, or is not a Short**. A weak hook cannot produce a true 0.

**First diagnostic in Studio:** `Shown in feed` (times the Short appeared in the Shorts feed).

- `Shown in feed` ≈ 0 → distribution problem — run the ladder in §3.
- `Shown in feed` high + "chose to view" low → hook problem — that yields dozens–hundreds of views, not 0.
- Public counter can lag/freeze while views are verified (see §5) — confirm in Studio Analytics / Realtime before concluding 0.

**SIGNAL — public views vs engaged views.** Public view counts run higher than engaged views (the metric that counts for YPP): Agentio measured 550 organic Shorts in 2026 and found public views averaging ~65% above engaged views. Compare like with like when judging performance across videos.

## 2. Diagnostic Ladder — All Documented Causes of 0 Views

Run top to bottom. Stop at the first hit; fix it; re-measure over days, not hours.

| # | Cause | Evidence | How to check |
|---|---|---|---|
| 1 | **Not actually a Short** — 16:9, or >3 min. Square/vertical ≤3 min, uploaded ≥15 Oct 2024 = Short. (Official Artist Channels: the same rule applies from 8 Dec 2025 — Help 15424877, re-read live 23 Nov 2026.) A 16:9 video never enters the Shorts feed. | FACT — Help 15424877 | Studio → Content → Shorts tab; open youtube.com/shorts/[ID] — a non-Short redirects to the watch page |
| 2 | **1–3 min Short + active copyright claim = blocked globally.** "Any Short that is over one minute in duration with an active copyright claim of any type… will be blocked globally… will not be playable or recommended… no penalties to your channel." Under 60s the block does not apply. | **CONFLICTING — see §2a.** Help 15424877 (re-verified live 23 Nov 2026) still says blocked. A second Help page reportedly says otherwise. Check the Restrictions column on the actual video. | Studio → Content → Restrictions column ("Claims"). Remove claimed content, dispute if wrong, or shorten to <60s |
| 3 | **Reused / repetitive / scraped content — reduced feed reach (Oct 2026) and/or spam removal.** See §3 — the most likely cause for a clip channel. | FACT — Oct 1 2026 TeamYouTube post; Spam Policy 2801973 §7 | Audit whether each Short adds commentary/storyline; compare Shorts-feed traffic before/after 1 Oct 2026 |
| 4 | **Visibility: Private / Unlisted / Scheduled.** Only Public videos are recommended. | SIGNAL (high-confidence; no single Shorts-specific Help sentence found) | Studio → Content → Visibility column |
| 5 | **Still processing / under checks.** HD/4K takes longer; copyright/ad-suitability checks run in the background. A short clip is normally minutes, not days. | FACT (general processing) | Studio status; watch-page Quality menu — missing HD = still processing |
| 6 | **Made for kids (audience setting).** Made-for-kids videos are recommended alongside other kids' videos and lose comments, notifications, personalized ads. NOT confirmed to remove a Short from the Shorts feed — do not claim that. | FACT — Help 9527654 | Studio → Content → Audience. Never falsely set "not made for kids" — FTC/COPPA risk |
| 7 | **Community Guidelines / age restriction / removal / strike.** Violating content is removed; age-restricted has limited distribution. | FACT — Help 1311392 | Studio → Content → Restrictions; email from YouTube |
| 8 | **Topic / audience mismatch + competition.** Low global interest, or stronger competing Shorts, means few/no impressions even with decent metrics. | FACT — Help 11914225 "external factors" | Studio Analytics → Traffic sources / Reach; compare "Shown in feed" across topics |
| 9 | **View-count verification lag (looks like 0, isn't).** See §5. | FACT — Help 2991785 | Compare public count vs Studio Analytics / Realtime |
| 10 | **Thumbnail / title — NOT a cause of 0 in the feed.** Shorts autoplay; there is no thumbnail click. Title/description matter for Search and the channel page, not feed distribution. A misleading title/thumbnail is separately a Spam Policy violation ("malicious clickbait"). | SIGNAL | Fix titles for search, not for feed 0s |

**NOT FOUND — do not assert:** no official source states that lack of phone verification, or a "new account limit", blocks Shorts distribution. No official source states a fixed "24–48 hours before the first push" rule. Both are creator folklore.

### 2a. The Content ID Claim Conflict — Read Before Acting on Cause 2

**What the main Help page says (verified live 23 Nov 2026):** Help 15424877, "Understand three-minute YouTube Shorts", still states that any Short over one minute with an active copyright claim of any type, including manual claims, "will be blocked globally on YouTube" — not playable, not recommended, not eligible for monetization, no penalty to the channel.

**What a second Help page reportedly says:** the "Create YouTube Shorts" page (Android) reportedly states that Shorts longer than one minute with an active copyright claim "will no longer be automatically blocked and may remain playable" — checked 19 Nov 2026 by an independent guide (postnext.io). This matches a Sep 24 2026 relaxation that was reported and then apparently reverted.

**Status: CONFLICTING / UNVERIFIED.** YouTube's own pages disagree as of 23 Nov 2026, and the relaxation claim could not be confirmed on the main Help page. **Round 2 re-check, 23 Nov 2026:** Help 15424877 was re-read live again today — the blocked-globally language is still present, word for word ("Any Short that is over one minute in duration with an active copyright claim of any type, including manual claims, will be blocked globally on YouTube"), and the page's FAQ repeats it. Do **not** state either version as settled fact. Practical rule until the pages agree: treat a claim on a Short over 60 seconds as a **risk to playback and earnings** — keep the Short under 60 seconds where audio/footage could trigger a claim, or use only audio you own. **Re-check date: 2026-12-23** — re-read Help 15424877 and the Create Shorts page, and update this section.

## 3. The Decisive Factor — Oct 1 2026 Originality Update + Reused-Content Policy

**FACT — What changed (TeamYouTube, JJ, 1 Oct 2026):**
https://support.google.com/youtube/thread/470890423?hl=en&msgid=470895343

> "To improve the Shorts experience for everyone, we're updating our recommendation systems to further prioritize original content and reduce the reach of content re-uploaded from other creators without adding anything of your own."
> "Channels identified as primarily aggregating or re-uploading other creators' videos without significant changes will likely see less distribution within the Shorts feed. If you use clips from another creator, make sure you're adding real value through your own original commentary, unique edits, or storytelling."
> "Rather than making minor technical edits or template-based changes simply to alter a video, focus on bringing your own voice, storytelling, or distinct point of view to the conversation."

No rollout date, no threshold for "primarily", no notification mechanism, and **no mention of permission, credit, or clipping programs at all** — there is no official carve-out for "with permission" clip channels.

**FACT — Reused content (Help 1311392):**

> "This policy applies even if you have permission from the original creator. Reused content is separate from YouTube's Copyright enforcement, which means it's not based on copyright, permission, or fair use."

- The test: "We allow reused content if viewers can tell that there's a meaningful difference between the original video and your video." It applies to the **channel as a whole**; monetization may be removed from the entire channel.
- **Allowed:** clips for critical review; a movie scene with rewritten dialog/voiceover; **replays of a sports tournament where you explain the moves a competitor did to succeed** (the direct analogue for gameplay); reaction videos where you comment; "Edited footage from other creators where you add a storyline and commentary"; content primarily featuring the uploader; reused content where the creator is visible or explains how they added to it; edited footage with effects demonstrating substantive editing unique to the channel.
- **NOT allowed:** "Clips of moments from your favorite show edited together with little or no narrative"; "Short videos you compiled from other social media websites"; "Collections of songs from different artists (even if you have their permission)"; "Content uploaded many times by other creators"; "Promotion of other people's content (even if you have permission)"; downloaded/copied without substantive modifications; **"Content that gets views from mostly non-verbal reactions to your videos without added voice commentary"**; pitch/speed-changed songs otherwise identical.
- **Generic/repetitive ("inauthentic", renamed from "repetitious" 15 July 2025 — clarification, not a new policy):** content that "looks like it's made with a template, or that may feel repetitive to viewers after watching several videos in a row"; similar/repetitive content with low educational value, commentary, narratives, or minimal variation; image slideshows, templated storylines, scrolling text with minimal narrative; AI content from generic templates without the creator's original insights.

**What this means for a clip channel's current format:** a borrowed clip + burned-in subtitles + on-screen hooks, with no voiceover, no commentary, no storyline/thesis per video, is exactly the profile the Oct 1 update deprioritises — a moments compilation with little narrative, built from a template, where the borrowed clip IS the video. Permission from the original creators and credit lines protect against copyright claims; they do **nothing** for Shorts-feed distribution. Subtitles, hooks, crop, and layout are "minor technical edits" in YouTube's words.

## 4. View-Count Verification Lag and Known Incidents (FACT)

- Help 2991785: "On some videos and channels, your metric count might seem frozen or not show the metrics that you expect… To verify that metrics are accurate, we may temporarily slow down, freeze, or change your metric count, and discard low-quality playbacks." Low-quality examples: same video on several devices/tabs. "It can take several days for verified metrics to fully update." Metrics "may take time to appear" in the first few hours.
- Practical reading: a **frozen-but-nonzero** count = verification queue. A **true 0 with Shown in feed = 0** = no distribution, not verification. Self-watching on multiple phones will not move the number — those plays are discarded.
- Confirmed incidents: **6 Jan 2026** Analytics syncing issue (APAC, gaps hours–couple days, fixed 6 Feb 2026); **24 May 2026** views dropping in Studio Analytics (fixed same day, views still counted correctly). **No YouTube-confirmed Shorts-specific "0 views" bug was found for 2025–2026.** Jul–Sep 2026 user reports of "Shown in feed = 0" are unverified user reports, not a confirmed bug — do not diagnose a channel as "bugged" on that basis alone.

## 5. The Fix — Legitimate, in Priority Order

1. **Add your own voice as the point of the video (THE fix).** The creator on camera, or their voice throughout, with commentary that IS the video — explaining why the play worked, what the streamer did wrong/right, the lesson, the story. Voiceover that only narrates/describes what is already visible does NOT count (SIGNAL — Creator Insider Oct 1 2026 video). The sports-replay analogue is the model: "explain the moves a competitor did to succeed."
2. **One storyline/thesis per Short, not a moment.** A moment with no narrative is the named violation. Every Short answers one question or tells one mini-story with a payoff.
3. **Keep the borrowed clip short relative to your added value.** The commentary must be the bulk of the experience, not a caption on someone else's clip.
4. **Mix in fully original Shorts.** The Oct 1 test is channel-level ("primarily aggregating"). Own gameplay, own face/voice, no borrowed footage — these prove the channel is not primarily a re-upload channel. Reach is re-evaluated when a channel shifts to original content (SIGNAL — Creator Insider Oct 1).
5. **Keep clips <60s where audio/music could trigger Content ID** (see §2 cause 2 and §2a), or use only audio you own.
6. **Keep permission + credit anyway** for copyright safety (a claim/takedown is a separate risk) — but never present permission as the justification to YouTube.
7. **Do not use the original creator's branding/thumbnail/title to imply the channel is theirs** — impersonation is prohibited (Fake engagement policy 3399767).
8. **Check Studio before judging:** Shown in feed, chose-to-view %, traffic sources, Restrictions column, audience setting, visibility. If all views come from the channel page, the feed is not testing it.
9. **Judge over 30 days, not 24 hours** (see §7). Apply the lesson to the NEXT Short — do not delete/re-upload the flop.

## 6. What NEVER Works — Against Policy (FACT)

- **Fake engagement policy (Help 3399767):** "YouTube doesn't allow anything that artificially increases the number of views, likes, comments, or other metrics either by using automatic systems or serving up videos to unsuspecting viewers." Banned: links to/promotion of view-inflating services, view-count/subscriber gaming sites, sub4sub (offering to subscribe only if they subscribe back — encouraging viewers to subscribe/like/share/comment is allowed), content featuring a creator purchasing views. "Page traffic found to be artificial will not be counted on YouTube and can lead to strikes on your account." Hiring a promoter does not shield you. Penalty ladder: removal + email; first violation likely a warning; **3 strikes within 90 days → channel may be terminated.**
- **Spam Policy (Help 2801973):** engagement manipulation (repetitive/templated content to inflate engagement via bots/coercion/rewards, coordinated sub-for-sub); automated/synthetic mass-production ("churn out high volumes of similar content with minimal changes"); scraped content (re-posting others' material "without adding anything of your own"); detection evasion (speeding audio, heavy filters, cropping/mirroring to bypass detection); malicious clickbait (misleading titles/thumbnails/descriptions).
- **Deleting/re-uploading:** Todd Sherman (YouTube Shorts product lead, Creator Insider Aug 2023, via TechCrunch): recommended against deleting/reposting a Short to make it take off — "There is a risk there that that gets seen as spam in our systems." Re-uploading the same video repeatedly is also the textbook scraped/repetitive pattern.
- **Buying views fails twice:** the bought plays are discarded as artificial traffic, and the channel risks strikes/termination.

## 7. Realistic Expectations — New Channel (SIGNAL, no official figure exists)

- **vidIQ First 10 Videos Study (28 Jul 2026; 448,413 new channels across the Shorts and long-form cohorts, created Jan–Jun 2025, ≥10 uploads in 90 days):** median first Short **1,362 views in 30 days**; fifth 1,275; tenth 1,344; best of first 10 **8,832**; **86.5%** had one of their first 10 reach 1,000 views within 30 days. https://vidiq.com/research/youtube-first-10-videos-study/
  - Caveat: the cohort is selected for persistence (≥10 uploads in 90 days). A 2-week-old channel below that activity level is not described by the median — but sustained 0–5 across several Shorts is **well below the typical new-channel outcome and warrants the §2 diagnostic**, not "slow start".
  - Shorts show no incremental growth across uploads 1→10 (1,362 → 1,275 → 1,344); growth comes from outlier videos. Medians are vidIQ's approximate percentile estimates, not exact counts.
- **SocialInsider (3M Shorts, 56k accounts, Jan–Dec 2025):** average views by age — 1–5 days 833; 5–10 days 1,786; 10–15 days 150; 15–20 days 555; 20–25 days 500; **25–30 days 3,310 (largest window)**. Many Shorts spike weeks after publishing. Judge a Short over 30 days. https://www.socialinsider.io/blog/how-long-does-it-take-for-yt-shorts-to-get-views/
  - Caveat: these are per-window **averages**, and the sequence is noisy (150 in days 10–15 vs 3,310 in days 25–30) — treat the shape as directional, not as a schedule. A counterweight: OverseerOS tracked 9,982 Shorts older than 30 days (Nov 2026) and found the median late gain was only 57 views, and no Short starting below 1,000 views gained another 1,000 in the window. Late spikes happen; large late rescues are rare. Judge at 30 days, but do not wait on a flop hoping for one.
- **How the feed works (FACT — Help 11914225):** ranked per viewer on performance (% chose to view, avg view duration, avg % viewed, likes, post-watch surveys) + personalization (history, topics, trending audio). External factors: topic interest, competition ("Even if you have good metrics on your Short, you may get fewer impressions if Shorts from other channels are performing even better"), seasonality. "There is no minimum posting cadence required for your videos to perform well." **Seed audience (FACT — Todd Sherman, Creator Insider Aug 2023, via TechCrunch):** the system finds "a set of people that may enjoy your video" and "depending on how that goes, it may get a lot more traffic or it may taper off" — "the audience is the algorithm." No published seed size, threshold, timetable, or 100/300/2,000-view tier — any guide giving a fixed number is inventing it. One underperforming video does not penalize a channel overall (Help + Official Blog 6 May 2025 myths post).

## 8. Workflows

### 8a. Per-Video 0-View Diagnosis (run when a public Short is at 0 after 24h)

1. Is it Public? (Visibility column.) If scheduled/private/unlisted — not a failure; wait for publish.
2. Is it in the Shorts tab in Studio? Open youtube.com/shorts/[ID] — redirect = not a Short (§2.1).
3. Restrictions column: any claim/flag? 1–3 min + claim = blocked or at risk (§2.2, §2a).
4. Audience setting: made for kids by mistake? (§2.6)
5. Studio Analytics: Shown in feed = ? Chose-to-view = ? Traffic sources = ?
6. If Shown in feed ≈ 0 and 1–5 pass: the cause is §3 (reused-content reach cut) or §2.8 (topic/competition). Fix the FORMAT (§5), not the upload.
7. If Shown in feed > 0 and chose-to-view low: hook/first-2-seconds problem — fix the next Short's opening, not this one.
8. Log the verdict per video (video, date, Shown in feed, chose-to-view %, cause, action) — never diagnose from memory.

### 8b. Pre-Upload Checklist (every Short, before publish)

- [ ] Vertical/square, ≤3 min, and if >60s, audio is claim-free (or accept the Content ID block risk knowingly — see §2a)
- [ ] Public (not scheduled-until-later confusion — scheduled is fine, but judge views only after it goes public)
- [ ] Audience: NOT made for kids (unless genuinely kids-directed)
- [ ] **Originality gate: does this Short contain the creator's own voice/commentary as the point, with a storyline/thesis?** If it is a bare moment-clip with subtitles only, it goes out knowingly as a low-reach format — flag it, do not expect feed distribution
- [ ] No bought views, no sub4sub, no misleading title/thumbnail, no re-upload of a deleted flop
- [ ] First comment timed per your channel rule; description passes your description checklist

### 8c. Weekly Re-Check (every Sunday)

- Re-read Shown in feed + views for every public Short older than 7 days; note any late spike (25–30 day window).
- Re-audit the channel mix: what % of the last 10 Shorts carry own voice/commentary vs bare clips? If bare clips are the majority, the channel is still in the Oct 1 deprioritized profile.
- Re-check the Restrictions column on every public Short (claims can land late).

## Appendix A. Worked Example — One Channel's 22 Nov 2026 Snapshot (Dated, Not Universal)

A GTA VI clips channel, ~2 weeks old, 5 subscribers, verified 22 Nov 2026 14:31 PKT via yt-dlp. Kept here only as a worked example of how the §8a diagnosis reads on real numbers.

- First public Short — **1,459 views** (public Nov 20).
- Second public Short — **326 views** (public Nov 21).
- One clip — **REMOVED by the uploader** (was 5 views on Nov 21 23:43; verified gone on both the Shorts URL and the watch URL). Who removed it is unknown.
- One clip — deleted on the owner's order; re-upload parked (daily upload limit).
- Everything else was **SCHEDULED, not public** — 0 views in Studio is normal for these, not a failure. Do not diagnose a scheduled video.

**Reading (as of 22 Nov 2026):** the feed IS testing the channel (1,459 and 326 views) but weakly, and the pure moment-clips stalled at 0–5. That pattern — some distribution, very low ceiling, worst on pure moment-clips — points at §3, not at a bug or a ban. Do not reuse these numbers as benchmarks; they are one channel on one date.

## 9. Sources (all re-checked 23 Nov 2026 unless noted)

- Oct 1 2026 originality update — TeamYouTube (JJ): https://support.google.com/youtube/thread/470890423?hl=en&msgid=470895343
- Reused / generic-repetitive / inauthentic content — Help 1311392: https://support.google.com/youtube/answer/1311392
- Search & discovery tips — Help 11914225: https://support.google.com/youtube/answer/11914225?hl=en
- How engagement metrics are counted — Help 2991785: https://support.google.com/youtube/answer/2991785
- Three-minute Shorts — Help 15424877: https://support.google.com/youtube/answer/15424877 (re-read live 23 Nov 2026 — blocked-globally language still present)
- Copyright claims — Help 6013276: https://support.google.com/youtube/answer/6013276
- Spam Policy — Help 2801973: https://support.google.com/youtube/answer/2801973
- Fake engagement policy — Help 3399767: https://support.google.com/youtube/answer/3399767?hl=en
- Audience setting — Help 9527654: https://support.google.com/youtube/answer/9527654
- YPP policy questions Jul 2025 — TeamYouTube: https://support.google.com/youtube/thread/356734251/response-to-creator-questions-about-ypp-policies-july-2025?hl=en-GB
- TechCrunch, Shorts algorithm (Todd Sherman), 25 Aug 2023: https://techcrunch.com/2023/08/25/youtube-demystifies-the-shorts-algorithm-views-and-answers-other-creator-questions/
- vidIQ First 10 Videos Study, 28 Jul 2026: https://vidiq.com/research/youtube-first-10-videos-study/
- SocialInsider, how long Shorts take to get views (3M Shorts, 2025): https://www.socialinsider.io/blog/how-long-does-it-take-for-yt-shorts-to-get-views/
- OverseerOS, do Shorts get views after 30 days (9,982 Shorts, 8 Nov 2026): https://www.overseeros.com/blog/do-youtube-shorts-get-views-after-30-days
- Content ID conflict — postnext.io, YouTube Shorts length (checked 19 Nov 2026): https://postnext.io/blog/youtube-shorts-length/

## Changelog

- **v1.1.0 — 2026-11-23 (Round 2):** Help 15424877 re-read live again (23 Nov 2026) — the blocked-globally language is still present word for word; §2a updated with the re-confirmation, re-check date stays 2026-12-23. Added the Official Artist Channels date (8 Dec 2025) to Cause 1. Re-tested the ladder on 2 fresh scenarios (see TEST-LOG.md): both reach the right diagnosis. Frontmatter description rewritten as a hook.
- **v1.0.0 — 2026-11-23:** Universal publish version. Channel ground truth moved to dated Appendix A; the fix's voice requirement generalised from one channel's host to "the creator's own voice/commentary"; Content ID Sep 24 2026 relaxation re-checked and marked CONFLICTING with a 2026-12-23 re-check date (Help 15424877 re-read live 23 Nov 2026 still says blocked); vidIQ sample corrected to 448,413 channels (Shorts + long-form cohorts); SocialInsider figures re-verified with a noise caveat and an OverseerOS counterweight added; engaged-vs-public views distinction added. Ladder tested on 2 scenarios (see TEST-LOG.md): both reach the right diagnosis.
