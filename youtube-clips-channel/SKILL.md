---
name: youtube-clips-channel
description: Run a game-clips YouTube channel end to end — sourcing, written permission, transformation, music hygiene, SEO, publishing, ban safety and strike response — so the channel grows without strikes, termination or a refused monetisation application. For anyone clipping other creators' footage.
version: 1.1.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
updated: 2026-11-23
---

# YouTube Clips-Channel Operator

Run one game-clips YouTube channel — Shorts plus compilations — from sourcing to publish, without getting the channel struck, terminated or refused monetisation.

Use this skill for every clips-channel task: channel setup, video production, publishing, SEO, safety checks, strike responses and visual generation. It is the clips-channel specialist. For a general original-content channel (scripts, retention, API-driven pipeline), use the general `youtube-operator` skill instead — the two do not merge: this one exists because clipping other people's footage carries copyright, reused-content and strike risks a normal channel never faces.

**Worked example used throughout:** GTA VI. Every GTA VI term, number and source in this skill is a dated worked example of the method, not a universal fact. Swap in your game and re-run the verification steps — never carry the example's keywords, hashtags or view counts into another game.

## Configure first — fill every placeholder before any upload

Nothing in this skill works until these are set. Keep them in one config file you can re-read in one glance.

- `[CHANNEL_HANDLE]` — the channel handle, e.g. `@yourchannel`.
- `[CHANNEL_ID]` — verify it in Studio before you touch anything.
- `[GAME]` — the one game this channel covers (see the hard rule below).
- `[GAME_TAGS]` — the game's 2–3 canonical spellings, e.g. `GTA 6`, `GTA VI`, `GTAVI`.
- `[REMOVAL_EMAIL]` — a dedicated public contact email for removal requests. Never reuse another channel's contact address.
- `[BRAND_BG]`, `[BRAND_ACCENT_1]`, `[BRAND_ACCENT_2]`, `[BRAND_TEXT]` — background, two accent and text colours. Two colours maximum on any visual, flat vector, generous empty space.
- `[CHANNEL_MARK]` — one mark, described in one sentence, used everywhere (profile picture, banner, watermark, thumbnails).
- `[HASHTAG_LINE]` — the locked 4-tag line for every video: two game tags + one community tag + the clip's creator tag, which changes per video (see Hashtag sets).
- `[SUBSCRIBE_LINE]` — the one locked subscribe sentence used in every description.
- `[OWNER]` — the person who approves visuals and videos before publish (see the approval gate below).

## The two gates — permission and monetisation are separate questions

Most clips-channel advice collapses these into one. They are two independent gates, enforced by different parties, with different failure modes. Passing one never passes the other.

| | Copyright gate | Reused-content gate |
|---|---|---|
| Who enforces | The rights holder, via Content ID claim or manual takedown | YouTube, at monetisation review |
| What it decides | Whether the video stays up and who earns from it | Whether the *channel* can monetise at all |
| Fixed by | Written permission, a licence, or removal | Genuine transformation — your commentary, story, analysis |
| Failure mode | Claim, strike, takedown | YPP application rejected, monetisation removed channel-wide |
| Permission helps? | Yes — it is the fix | No — the policy applies "even if you have permission from the original creator" (YouTube Help 1311392, verified live 2026-11-23) |

A paid clipping-campaign brief and YPP ad revenue are two different businesses. A campaign pays you per view under its own terms; YPP pays you for a channel YouTube considers original. Doing the first well does not qualify you for the second. Plan income accordingly — campaign pay is the durable income for this material, not YPP ads.

## Channel identity and brand

- Open the channel and confirm the handle and channel ID before you touch anything.
- Keep the brand palette to the four configured colours. Keep every visual flat vector, two colours only, with generous empty space. Reject any visual that is cluttered, 3D rendered, or full of extra objects. Regenerate it simpler and flatter instead of accepting it.
- Never redraw or copy the game publisher's logo. Never use another brand logo. Never put a fake earnings figure or a fake claim on a visual or in copy.
- Use these exact sizes for every brand asset.
  - Logo and profile picture, 800 by 800 px PNG. It displays as a circle, so keep the emblem and text clear of the corners. Check legibility at 98 by 98 px, the smallest display size.
  - Logo master, a high-quality separate 1 to 1 PNG at maximum detail. Generate it as its own file, not as a crop of the logo. Use it for permanent reuse across posters, thumbnails and merch.
  - Channel banner, 2560 by 1440 px JPG or PNG under 6 MB. Keep all text and the logo inside the safe area of 1546 by 423 px dead centre.
  - Video watermark, 150 by 150 px PNG with a transparent background. Use a simplified monogram only, legible at tiny size.
  - Shorts thumbnail, 1080 by 1920 px, 9 to 16 vertical. Use an accent frame, the channel mark in the top corner, and big readable moment text.
- **Owner approval gate (configurable, not optional):** every new visual and every video is approved by `[OWNER]` before it goes on the channel. Approving caption text is not approval of the visual. Nothing uploads without the owner's approval of the visual itself. Approval never auto-publishes: the publish step needs an explicit per-video yes, every time. Set this gate in your config — who approves, and in what form — before launch.
- Read every word and number on every visual against the brief before you hand it over. A typo, a wrong word, a duplicated word or cut-off text means regenerate the visual before it ships.

## Hard rule, one game only

- Publish content about `[GAME]` only. Never label `[GAME]` footage as another title, and never label another title's footage as `[GAME]`. Misleading metadata is a removal and strike risk.
- Never use a `[GAME]` hashtag, title or claim on other-game footage. Never use expired framing ("before [GAME]" after launch, farewell framing after release). Old videos carrying expired framing are ranking assets — leave them alone.
- Treat launch facts as dated snapshots, not permanent facts. Record the launch date, platforms and any launch-week peak numbers with their date and source, and re-verify before citing them again.

## How YouTube ranking works

- YouTube runs separate ranking systems for Search, Home, Suggested and Shorts. There is no single algorithm, no published weighting and no published search-volume data. Treat any exact ranking percentage or exact monthly search volume quoted anywhere as invented.
- Rank Search by relevance first, then engagement on that query. Relevance means how well the title, description and video content match the query. Search results are not a list of the most-viewed videos for that search. A zero-subscriber channel can rank for a specific long-tail query when relevance and post-click behaviour beat the incumbents.
- Rank Home by performance with similar viewers, watch and search history, and how often a viewer watches the channel or topic. A new channel gets almost no Home traffic until it has proven satisfaction with lookalike audiences. Do not plan around Home in month one.
- Rank Suggested by what viewers are most likely to watch next after the current video, and by what is often watched together. Win here with topical adjacency, playlists, series numbering and end screens that continue the session.
- Rank the Shorts feed by the percentage of viewers who chose to view, average view duration, average percentage viewed, and likes plus post-watch surveys. The feed has no click, so viewers vote by watching or swiping. Loop and rewatch behaviour and shares are the strongest signals in creator guides.
- Rank Shorts in Search by how well the metadata matches the search and whether viewers click and watch. A Short can rank in search independently of the feed, so optimise for both the feed hook and the search keyword.
- Treat tags as minimal. YouTube states that tags play a minimal role in discovery. Use them mainly for commonly misspelled terms.
- Treat velocity as an outcome, not a ranking input. A new upload is shown to a small test audience and scaled only when click-through and retention beat the bar. Treat the first 24 to 48 hours as a test, not a verdict.
- Treat upload frequency as a learning strategy, not a ranking boost. YouTube states there is no minimum posting cadence required for videos to perform well.
- Treat Shorts watch time as not counting toward the long-form watch-hour threshold. Shorts have their own views path.
- Treat Shorts performance as not harming long-form recommendations. The two were decoupled, according to YouTube.
- Put the hook in the first 1 to 2 seconds of every Short. The first seconds are the thumbnail in the feed. Put the spoken keyword and on-screen text in the first 3 seconds.
- **Score the hook before you cut.** Write 3–5 hook options for each video, score each 1–5 on (a) specific moment named, (b) curiosity gap, (c) keyword in the first words. Cut only the top scorer. A hook that scores under 10/15 gets rewritten, not filmed.
- **Lint title + thumbnail as one pairing.** Read them together: no duplicated words between them, no promise in either that the video does not keep, no vague word ("crazy", "insane") doing the work a specific moment should do. If the thumbnail says it, the title does not repeat it.
- Keep Shorts tight — 15 to 30 seconds completes best, longer only when every second earns it; length alone barely moves views (the hook does), so never stretch a clip to fill a length target. Keep clips at 59 seconds or shorter whenever any claimed audio is possible. See the music section.
- Use titles of 100 characters maximum, and aim for 30 to 60 characters for Shorts (the pack standard, reconciled from Returbe 41–70 gaming / OverseerOS 20–40 / AIR 30–50 — see your SEO companion skill), with the keyword in the first 3 to 5 words. A shorter specific title is fine — never pad a title to reach the band, and never butcher a specific title to fit it. Use one primary keyword phrase at the start, in natural language. Use one emotion or superlative, not three. Prefer specific moments over general phrases. Never use all-caps whole titles. Never put #Shorts in a title. No emoji in a Shorts title — Returbe (63,480 videos) found emojis have no measured effect (9.6% outliers vs 11.1% average), and YouTube's own line is "Limit ALL CAPS and emoji". Never promise a moment the clip does not keep. Number a series only after 3 or more Shorts exist in it.
- Put the keyword and the hook in the first 100 characters of the description, which is the preview. Keep a Shorts description to 1 to 2 sentences of visible copy (50 to 150 characters) plus the credit line and the locked hashtag line, with the keyword in sentence one. Keep tags to 5 to 10 per video inside the 500-character tags limit. Hashtags are the locked line plus an optional moment tag as 5th and optional #Shorts as 5th or 6th, never more than 6 total. More than 60 hashtags means all are ignored, and misleading hashtags can get the video removed. Shorts description URLs are not clickable since 31 Aug 2023 — the link renders as plain text; the click path is the Related Video link set in Studio.
- Add accurate captions and correct the auto-captions. Say the keyword aloud and put it on screen. Pin a comment that asks a question on each Short and reply to early comments. Do not pin a keyword list or a link dump.
- Judge Shorts by average percentage viewed and viewed versus swiped, not by raw views. Judge long-form by click-through rate, average percentage viewed and session contribution. Judge a series against the channel's own median, not against other channels — a video that beats your median by 2x is a winner even at small absolute numbers; a video below median is cut even if its raw views look fine.

## Keyword tiers — method first, worked example second

**Method (applies to any game):**
- Verify every term before you publish by searching it signed out and inspecting the top 10 results. Ask whether the top results are exact-match titles, big channels or old videos. That two-minute check is the real competition score. YouTube publishes no search volumes, so no numeric volumes appear in this skill.
- Tier 1: specific moment types with clear search intent, weak incumbents. Attack first.
- Tier 2: proven demand, stronger incumbents. Build toward them once the channel has watch data (weeks 3–4).
- Tier 3: saturated, vague or misleading. Never lead with these.
- Time-boxed terms (launch-week glitches, pre-launch questions, "where is X" before guides exist) carry an expiry date in your keyword file. Past the date, re-verify or drop them — never post an expired term on autopilot.
- Cover spelling variants in every description and in tags, never in the title.

**Worked example — GTA VI, keyword research snapshot November 2026.** Use as the shape of a Tier 1/2/3 file, not as live keyword advice. Re-run the signed-out top-10 check before using any of these.
- Tier 1: `gta 6 glitch` (one specific glitch per Short, exact glitch name in title); `gta 6 funny moments` (lead with the moment, not the phrase); `gta 6 fails` (single fail, FAILS in title); `gta 6 bugs` (second keyword only — title says glitch, description and hashtags carry bugs); `gta 6 lucia` (Lucia plus a specific verb or moment, never bare); `gta 6 npc` (the NPC doing something specific is the title); `gta 6 police chase` (chase plus outcome, never a star count); `gta 6 wtf moments` (only when genuinely unbelievable); `gta 6 funny` (keyword and hashtag only, never the lead title phrase); `gta 6 clips` (description and channel positioning, not most titles); `gta 6 alligator` (one Short per moment, only when the visual is unmistakable).
- Tier 1, deleted — do not lead with these: `gta 6 unlucky moments`, `gta 6 painful clips`, `gta 6 crazy jumps and best falls`, `gta 6 5-star police chase`, `where is X in gta 6`, `how to fix X in gta 6`. The first three may survive as long-form compilation labels, not Shorts lead terms. The guide terms are built toward in week 2 and later.
- Tier 2: `gta 6 funny moments compilation`; `gta 6 epic moments` and `epic wins`; `gta 6 best clips`; `gta 6 memes`; `gta 6 free roam`; `gta 6 gameplay`, `gta 6`, `gta 6 shorts`, `gta 6 map`, `gta 6 cars`, `gta 6 jason` (pair Jason with Lucia or a specific moment); `gta 6 ragdoll moments` (demoted from Tier 1 — top results were still the previous title at research time; build a compilation only once 3+ genuine clips exist); `gta 6 stunt fails` / `gta 6 stunt` (demoted — gap not proven demand; test with one Short, judge by feed performance, do not build a series without evidence); `where is X` / `how to fix X` guide terms.
- Tier 3: the game title alone as a title; any game term on other-game footage; single words such as funny, viral or trending as a title; platform/release-date terms when no such version exists; review/score terms (news-owned, dead within 48 hours); trailer/leak terms (pre-launch; leaks are a ban risk); download-size/preload terms (one-number answer, expires on launch day); online/multiplayer terms when no such mode exists at launch.
- Spelling variants for this game: GTA 6, GTA VI, GTAVI, Grand Theft Auto VI.

## Title formulas

Use one formula per video, with the primary keyword first, and keep every title at 100 characters or fewer. Shorts titles: aim 30 to 60 characters (the pack standard — see your SEO companion skill); a shorter specific title is fine, never pad to reach the band. Keyword in the first 3 to 5 words. Never put #Shorts in a title. No emoji in a Shorts title (Returbe: no measured effect; YouTube: "Limit ALL CAPS and emoji"). Full length and evidence rules live in your SEO companion skill, if you have one.

Worked example — GTA VI formulas (swap the game and moment; character counts script-verified 23 Nov 2026):
- `Ranking the FUNNIEST GTA 6 Moments` (34) — add the series number once 3+ Shorts exist
- `TOP 10 GTA 6 Fails` (18) — short is fine when the idea fits; use TOP 5 for Shorts
- `GTA 6 Lucia Moments That Broke the Game` (39) — add the series number once 3+ Shorts exist
- `GTA 6 NPC Walks Into Traffic` (28)
- `GTA 6 Police Chase Ends on a Roof` (33)
- `WTF Just Happened in GTA 6` (26)
- `GTA 6 NPC Walks a Pet Alligator` (31)
- `0% Skill, 100% Luck — GTA 6 Win` (31)
- `BEST GTA 6 Fails and Wins Compilation` (37) — long-form; add the series number
- `GTA 6 Glitch Breaks the Game` (28)

## Hashtag sets

**Method:** lock one 4-tag line and use it on every video, in the same order: two game tags + one community tag + the clip's creator tag (the first three are locked; the creator tag changes per video). A moment hashtag may be added as a 5th when a moment keyword genuinely applies, never displacing the four locked tags. #Shorts is optional as 5th or 6th, or omitted entirely, never first, never in the title. Never use viral, trending, funny or gaming alone as hashtags. Never use any game hashtag on other-game footage. Never use more than 6 hashtags. More than 60 hashtags means YouTube ignores all of them (Help answer 6390658).

**Worked example — GTA VI locked line:** `#GTA6 #GTAVI #GamingNews #[Creator]`, in that order. `#[Creator]` is the clip's creator tag — it changes per video and is mandatory on every video. (Round 2 fix: an earlier draft locked `#IShowSpeed` on every video, which contradicts the creator-only rule — never tag a creator who is not in the video.) Moment tags: `#GTA6Fails`, `#GTA6Stunts`, `#GTA6FunnyMoments`, `#GTA6Lucia`, `#GTA6PoliceChase`, `#GTA6Glitch`, `#GTA6Compilation`.

## Pinned comments, hearts and the first hour

- Pinning requires Advanced features; up to 24 hours after they are turned on to appear (Help answer 6000964). Until phone verification plus history or ID verification are done, the channel cannot pin — a live gate, not a preference. Check Studio, Settings, Channel, Feature eligibility. Until the gate opens, post the first comment anyway and pin it once the gate opens.
- A pinned comment cannot be set while a video is scheduled or private (reported, not verified against a live Help page). Write the pin text in advance; post it from the channel account the moment the video goes public, then pin it. Every scheduled Short needs a post-publish pin step.
- One pinned comment per video; pinning a new one replaces the old one. Default: pin your own question comment immediately after publish; occasionally rotate the pin to a standout fan reply.
- Links in Shorts comments are non-clickable since 31 Aug 2023. Never put a bare URL or a link-first line in a Shorts pinned comment. What is tappable in a Shorts comment: hashtags and @mentions. Name the next video by its exact title; the Related Video link is the actual click path.
- Pinned comment = one specific question tied to that clip (binary, this-or-that, or score), OR the answer to the obvious question, OR a correction or update note. Generic "Subscribe!" generates about zero engagement. Never a bare URL, never a promo or link-first line.
- Vary the pinned comment per video — the question must be specific to that clip. Posting the same pinned text on every Short is, on the face of the Spam Policy, "repetitive comments … to drive … engagement". No safe numerical threshold exists. Never automate identical pins across a batch.
- No official statement links pinned comments to feed ranking. The defensible claim is only that the pin is the most-read text on the video and the cheapest way to seed a thread. Do not cite third-party CTR or lift figures as fact — the ones circulating are self-labelled illustrative or have no methodology.
- Heart + reply in the first hour, every video (peer-reviewed study, Choi et al. 2025, doi:10.1145/3706598.3713521: creator hearts soon after publishing incentivised more commenting over time, greatest effect within the first 5 hours). A heart does NOT move a comment to the top, only pinning does, and YouTube publishes no guarantee a heart affects ranking. Heart broadly, not only top comments; a reply ending in a question doubles the odds of a second comment (anecdotal, reported).

## Community posts

- Do not wait for 500 subscribers — the subscriber rule was removed in 2023 (reported). Eligibility (Standard vs Advanced) is unresolved — check Studio, Settings, Channel, Feature eligibility.
- Use Posts for polls that pick the next clip or ranking, image posts teasing the next Short, and corrections or updates. 2 to 3 posts per week; posts under about 280 characters (reported, vendor claim, anecdotal).
- Do not budget Posts as a Shorts-view driver — no solid evidence they drive Shorts views; do not report any "% lift" figure as fact. Links in Posts are clickable only with Advanced features (reported). Images must be owned or permissioned.

## Playlists

- Create all playlists on day one, even before all videos exist. A playlist with 1 or 2 videos is fine. Build one playlist per series plus one per format: fails, stunts, funny moments, unluckiest moments, epic wins, physics/ragdoll fails, weekly compilations, and an all-Shorts playlist.
- Worked example — GTA VI playlist set (8): Best GTA VI Fails; GTA VI Stunts Gone Wrong; GTA VI Funny Moments; GTA VI Unluckiest Moments; GTA VI Epic Wins; GTA VI Ragdoll and Physics Fails; Best GTA VI Clips, Weekly Compilations; GTA VI Shorts, Daily Clips. Each description names the game, the moment type and the cadence, and promises credit to featured creators.
- Order the home page as follows: trailer, latest Shorts, fails playlist, stunts playlist, funny moments playlist, weekly compilations, and a best-of shelf added manually after day 30 with the top 6 performers.

## Channel keywords and upload defaults

- Set channel keywords in Studio, Settings, Channel, Basic info. The field holds about 500 characters. Use your Tier 1 and Tier 2 terms plus the game's full and short names.
- Worked example — GTA VI channel keywords: `gta 6 funny moments, gta vi funny moments, gta 6 fails, gta vi fails, gta 6 stunts, gta vi clips, gta 6 compilation, gta 6 epic moments, gta vi wins, grand theft auto vi, gta 6 shorts, gta 6 funny moments compilation`.
- Set upload defaults in Studio, Settings, Upload defaults. Use the Shorts description template from the ready texts section, the default tags below, category Gaming, language set to your audience's language, and the Standard licence.
- Default tags for Shorts — swap the last 2 or 3 per video for the video keyword: the top Tier 1 terms, the game tags, the primary keyword, the moment keyword, the game's full name. Add compilation/epic-moments terms to the default tags for long-form videos.
- Link the clip submission form first in the channel links, then the best playlist, then socials only when they are active. Never leave a dead link.

## Launch checklist in apply order

- Complete Phase 0 on day 0, before any upload.
  - Verify the channel by phone in Studio, Settings, Channel, Feature eligibility. This unlocks custom thumbnails and uploads over 15 minutes.
  - Finish the logo and banner and set the profile picture, banner and video watermark.
  - Paste the About text from the ready texts section. Set the links with the clip submission form first.
  - Set the channel keywords, country, language and category.
  - Set upload defaults with the Shorts description template and default tags.
  - Create all playlists.
  - Create the clip submission form. Ask for the clip link, the creator handle, a checkbox that says the creator gives the channel permission to feature and edit this clip with credit, and a contact. This form is the permission trail.
- Complete Phase 1 on days 1 to 2.
  - Produce 7 Shorts, one per Tier 1 keyword, plus long compilation number 1 and a 30 to 60 second trailer. Every clip needs written permission on file, on-screen creator credit, and the channel's own narration or ranking voiceover.
  - Design one thumbnail template for long-form, a freeze frame with 3 words or fewer and consistent font and colour, and one Shorts first-frame template with big on-screen text in frame 1.
- Complete Phase 2 on days 3 to 30.
  - Publish 1 Short per day, 2 per day maximum, spaced 4 to 6 hours apart. Publish a long compilation weekly.
  - Give every upload a keyword-first title (30 to 60 characters when the idea fits, never over 100), the template description, 5 to 10 tags, the locked 4 hashtags (plus an optional moment tag), a pinned comment with a question (posted after publish, pinned once Advanced features allow), and add it to its playlist within minutes. Link each Short to the long compilation in the description; name the compilation by its exact title in the pinned comment, because links in Shorts comments are not clickable.
  - Reply to every comment in the first hour for the first 30 days.
  - Run analytics reviews on day 10 and day 30. Rank Shorts by average percentage viewed and viewed versus swiped, not by views. Cut the worst series and double the best — judged against the channel's own median, not raw views.
- Complete Phase 3 from day 31.
  - Keep only the 2 winning series. Attempt Tier 2 head terms on the back of winners. Keep sourcing own gameplay plus licensed or submitted footage only.
  - Publish the trailer as the channel trailer for new visitors and add a best-of shelf.
  - Re-check YPP thresholds in Studio and audit the channel against the reused-content checklist before applying for monetisation.

## Realistic expectations

- Treat these numbers as third-party estimates, not guarantees. Growth is typically flat for the first 10 weeks, then one search or feed winner pulls the rest up.
  - 30 days: 100 to 500 subscribers on a daily Shorts cadence. A single viral Short can add thousands in a week, but do not plan on it.
  - 6 months: 200 to 800 subscribers is a realistic range for steady weekly long-form. Shorts-first channels can be faster on subscribers and slower on watch hours.
  - To 1,000 subscribers: typically 6 to 12 months and 20 to 50 videos.
  - Month 1 total: about 30 Shorts plus 3 to 4 long videos.
- Treat working at day 30 as average percentage viewed rising across Shorts, at least one Short with 70 to 80 percent average viewed, search impressions appearing in Studio under Reach and YouTube search, and one series clearly outperforming the others. The 70 to 80 percent band is an unverified third-party benchmark. Use it only as an internal target.
- Treat the monetisation thresholds as follows. YPP ad revenue currently needs 1,000 subscribers plus either 4,000 qualified watch hours in 12 months or 10 million qualified Shorts views in 90 days. An early tier needs 500 subscribers plus 3,000 hours or 3 million Shorts views (plus 3 valid public uploads in the last 90 days). Hitting the numbers only lets the channel apply. The reused-content review is a separate human review, and it is the real gate.

### YPP thresholds from 1 February 2027 — confirmed

YouTube announced this on 10 August 2026 on the official YouTube Blog (first significant YPP overhaul since 2018); confirmed against multiple independent write-ups of the announcement, November 2026. Confirm the live figures in Studio before planning around them — thresholds are the one number in this skill that moves by calendar date.

| | Until 31 Jan 2027 | From 1 Feb 2027 |
|---|---|---|
| Subscribers (full tier) | 1,000 | 1,000 (unchanged) |
| Watch-hour path | 4,000 qualified hours / 12 months | **8,000 qualified hours / 365 days** |
| Shorts-view path | 10M qualified Shorts views / 90 days | **20M qualified Shorts views / 90 days** |
| Early tier (500 subs) | 3,000 hours or 3M Shorts views | Unchanged |
| Shorts Creator Pool payout floor | None | 10M qualified Shorts views / 90 days, every month |
| "Active" channel definition | None | 1,000 qualified hours / 365 days, OR 1M Shorts views / 90 days, OR 2 long-form videos or 5 Shorts every 90 days |

Channels already in YPP keep their place, but must accept the updated terms in Studio by 31 January 2027. Shorts-feed watch hours never count toward the watch-hour threshold. Keep the long-form compilation path alive either way, because it is the more controllable route to watch hours.

## Ban safety system — one reconciled position on fair use

**The single position this skill takes, everywhere in it:** fair use is a legal defence you argue after a claim, never a licence you claim in advance. Credit does not create it, a disclaimer does not create it, and writing "used under Fair Use (Section 107)" in your About text or description does not protect you — it can read as an admission that you knew the material was someone else's, which can undermine an innocent-infringer argument on damages. Every ready text in this skill therefore uses neutral, factual attribution plus a removal contact, and never claims a fair-use licence. If any text in this skill or in your channel copy contradicts that, the neutral wording wins.

- Treat a disclaimer as almost no protection. YouTube states that there are no magic words to automatically apply fair use, and that including the phrase "no infringement intended" will not automatically protect you from a claim of copyright infringement. Credit will not by itself turn a non-transformative copy into fair use, and it does not mean you have permission. A disclaimer plus credit plus a removal email is still worth having, because it helps a human claimant choose contact or retraction over a strike, and it is honest attribution. It stops no Content ID claim, no strike, no termination and no reused-content rejection.
- Never write "no copyright infringement intended", "I do not own", or a Section 107 block as if it were a licence.
- **The per-clip evidence test.** For every clip, complete this sentence in one line before you cut: "This clip proves/illustrates [specific point], and my commentary adds [specific point]." If you cannot, the clip is entertainment, not commentary, and it weakens both your fair-use position and your reused-content position. Keep the one-liner in the source log.
- Treat reused content as a monetisation rule, not a strike. YouTube states that reused content refers to channels that repurpose content already on YouTube or another online source without adding significant original commentary, substantive modifications, or educational or entertainment value. The policy applies even when you have permission from the original creator, and it is not based on copyright, permission or fair use. It applies to the channel as a whole, and monetisation may be removed from the entire channel. Reviewers check the main theme, the most-viewed videos, the newest videos, the biggest watch-time share, the metadata and the About section. (YouTube Help 1311392, verified live 2026-11-23.)
- Treat these YouTube examples as the fail cases to avoid. Clips of moments from a favourite show edited together with little or no narrative. Short videos compiled from other social media websites. Collections of songs from different artists, even with permission. Content uploaded many times by other creators. Content downloaded or copied from another online source without any substantive modifications. Content that gets views from mostly non-verbal reactions without added voice commentary. Songs modified to change the pitch or speed but otherwise identical to the original song. Promotion of other people's content, even with permission. Content that exclusively features readings of other materials you did not create.
- Treat these as the pass cases to build toward. Clips used for a critical review. A movie scene where you rewrote the dialogue and changed the voiceover. Sports replays where you explain the moves. Reaction videos where you comment on the original video. Edited footage from other creators where you add a storyline and commentary. Content that primarily features the uploading creator. Reused content where the creator is visible in it or explains how they added to it. Edited footage with audio and visual effects on top that demonstrates substantive editing and shows it is unique to your channel.
- Treat inauthentic content as a second, independent reason to fail review. YouTube renamed repetitious content to inauthentic content on 15 July 2025. A single editing template applied to 100 clips is a double risk, reused and inauthentic. Vary the hook, the ranking criteria and the edit per video. The substance of each video must be materially varied and deliver creative, educational or other value — same intro/outro is fine, interchangeable videos are not.
- Treat the October 2026 Shorts reach change as a distribution risk. YouTube stated it further prioritises original content and reduces the reach of content re-uploaded from other creators without adding anything of your own. Crops, flips, speed changes, filters, transcribed captions, template-based changes and voice-over that merely narrates what is on screen are named as not enough. Commentary, analysis, unique editing and storytelling count.

## The four enforcement systems

- Treat a Content ID claim as a video problem, not a channel problem. Content ID scans every upload against reference files. On a match the rights holder policy applies: monetise, track or block. A claim is on one video and usually does not result in a strike or impact the channel. Accept it, trim or mute the claimed segment, replace the song, or leave it and lose that video revenue. Use Studio Erase song, Trim or Replace song to remove the claim without a dispute.
- Treat a dispute as a path that can escalate to a strike. The claimant has 30 days to respond to a dispute. When a dispute is rejected you may appeal, and the claimant then has 7 days to respond. When an appeal is rejected the claimant can submit a copyright removal request, and a valid removal request removes the video and gives the channel a strike. YouTube states directly that disputing a copyright claim without a valid reason can end in a removal request and a strike. A submitted dispute cannot be withdrawn, according to secondary sources. Dispute only on a real ground, such as written permission covering that use, a false match, public domain material, or a considered fair-use argument you accept the escalation risk for. Never dispute on credit, short length, not monetised, or "I bought the game".
- Treat a copyright strike as a channel-level penalty. One video means one strike at a time. Three copyright strikes in 90 days means the account, along with any associated channels, is subject to termination. Strikes expire in 90 days only when you complete Copyright School and the channel has fewer than 3 strikes. Copyright School is 4 questions, completed once. Without it a strike stays active. When a removal request was scheduled, you have 7 days to delete the content and avoid the strike. In all other cases deleting a video does not resolve a strike. The only three resolutions are Copyright School plus waiting 90 days, a retraction from the claimant, or a valid counter notification.
- Treat a counter notification as a sworn legal statement under penalty of perjury. You consent to US federal court jurisdiction, YouTube must share it with the claimant including your full legal name, physical address and phone number, and the claimant then has 10 US business days to show it has filed a lawsuit. Never file one to get a strike off when the claim was valid, or on a clip you knowingly took without permission. Fraudulent counter notifications can lead to account termination. Only file when you genuinely believe there was a mistake or misidentification or a real fair-use or licence case, and take legal advice first when the channel matters.
- Treat Community Guidelines strikes as a separate counter from copyright strikes. A warning comes first, typically, and you complete the optional policy training. The warning expires 90 days from when training is completed, not from when the warning was issued. A first strike means 1 week unable to upload, live stream, schedule a video to go public, create a Premiere, create custom thumbnails or posts, or create or edit playlists. A second strike in the same 90-day period means 2 weeks unable to post. A third strike in the same 90-day period means the channel may be permanently removed. Each strike expires 90 days from issue. Deleting content does not remove a strike, and a strike can be issued on deleted content. A single severe abuse can terminate a channel without warning. Appeal a termination in Studio within 1 year, with a maximum of 2 appeals.
- Treat spam and deceptive practices as a termination route that needs no 3-strike ladder. Misleading metadata or thumbnails, mass-produced or scraped uploads, bought engagement, sub for sub, comment spam, and channels dedicated to a violation can be terminated immediately. Spam is the largest stated cause of channel removals. Keep titles and thumbnails honest, keep uploads to 1 or 2 per day as a house rule, and never buy views or subscribers.
- Treat a Short over 1 minute with an active Content ID claim as blocked globally. (FACT, Help answer/15424877, re-read live 23 Nov 2026: "Any Short that is over one minute in duration with an active copyright claim of any type, including manual claims, will be blocked globally on YouTube.") One secondary source reports that from 24 Sep 2026 new over-1-minute Shorts with a claim are no longer automatically blocked — that claim could not be confirmed on the main Help page, so the two sources still conflict; stay under 60 seconds whenever claimed audio is possible. (See the Shorts diagnostics skill's §2a for the full conflict note.)

## Associated-channel risk

- Treat sharing one Google account across channels as high risk. YouTube states that at 3 copyright strikes the account, along with any associated channels, is subject to termination. A terminated person is prohibited from using, possessing or creating any other YouTube channels, and that applies to all existing channels. A Brand Account under the same Google account does not fix this, because it changes who can manage a channel, not who owns it in termination logic.
- Do not upload a single clip until isolation is done. At 0 subscribers and 0 videos the cheapest isolation is to create the clips channel clean on its own dedicated Google account.
- Create a new dedicated Google account for the clips channel only, with a new email address, a unique strong password plus a passkey, and a different recovery email and recovery phone from any other channel you run.
- Create the clips channel on that new account as a Brand Account channel. Do not add any other channel's account as an owner, manager or editor, and do not add the new account to any other channel. Keep no cross-ownership and no cross-management.
- Use a separate AdSense account for the clips channel when it is monetised, or do not monetise it at all. Never link the same AdSense or payee to two channels. One secondary source claims 20 or more channels sharing one AdSense account were terminated together in Sept 2025. That claim is unverified, from a single secondary source.
- Use a separate public contact email for the clips channel. Keep separate 2-Step Verification, backup codes and recovery details, stored separately from your other channels.
- Treat the transfer route as the slower option, only when the handle matters more than the clean break. Move the existing channel to a Brand Account, invite the new Google account as Owner, wait 7 days, make it Primary Owner, then remove the old account. A new owner must have been owner or manager for at least 7 days, and the person making the change must have been an owner for at least 7 days. AdSense does not move. When the destination Brand Account already has a channel, YouTube warns the existing channel will be deleted, so read that screen.
- Accept the honest limit. Even a fully separate Google account does not guarantee your other channels survive when the clips channel is terminated. The circumvention rule applies to the person, not the account, and YouTube detects related channels automatically by unpublished signals. Separation removes the automatic account-level trigger and the shared AdSense link, which is the strongest practical step available. Isolation must be done before any termination. Creating a new account or channel after a termination to get around it is itself circumvention.
- Rate the risk as high with shared accounts, medium after clean separation on a separate Google account plus a separate Brand Account plus separate AdSense done before any strike, and low after separation plus permission-only sourcing plus transformation plus music hygiene.

## First-hour strike and claim playbook

- Act on a Content ID claim in this order. Screenshot the claim in Studio, Content, Restrictions, See details, with the claimant, the segment and the policy. Decide in 10 minutes whether the claim is right. When it is right, accept it, or trim, erase song or replace song, or leave it and lose that video revenue. Dispute only on a real ground and within 5 days for the money rule, attaching the evidence in the dispute text. Remember you cannot cancel a dispute and the claimant has 30 days. When a dispute is rejected, stop and think before appealing. An appeal gives the claimant 7 days and a rejected appeal can become a removal request plus a strike. When you are already on 1 strike, default to not appealing a weak case.
- Act on a copyright strike in this order. Screenshot everything in the first 15 minutes. Open Studio, Dashboard, Active copyright strikes, and Content filtered by Copyright, See details. Check whether the removal was scheduled. When it was, you have 7 days to delete the video and avoid the strike. Complete Copyright School immediately, in minutes 15 to 30. This starts the 90-day expiry clock. Pause all uploads. Make private, not delete, any other videos using the same source creator, the same music or the same format, pending review. Audit the whole back catalogue for the same risk. In hour 1, email the claimant politely asking for a retraction, using the template in the ready texts section. Apologise, confirm the video is down or private, explain what you will change, and ask whether they will retract. Do not threaten, do not argue fair use in the first email, and do not file a counter notification in anger. Consider a counter notification only when the removal was a mistake or misidentification or a genuine fair-use or licence case, ideally with legal advice. Log the date, the claimant, the video, the strike number, the Copyright School completion date, the 90-day expiry date, the retraction email sent and the outcome. Set a calendar reminder for the expiry date.
- Never create a new channel, post the same video on another channel you run, or keep uploading the same format while a strike is active. That is circumvention and a route to a second or third strike.
- Act on a Community Guidelines warning or strike in this order. Read the email for the content, the policy and what it affects. Complete the policy training for a warning. Appeal from Studio or email when you think YouTube made a mistake. Do not delete the content when you are appealing it. Respect the 1-week or 2-week freeze. Reschedule anything that was set to private. Do not use another channel to post during the freeze.
- Act on a termination email in this order. Do not create a replacement channel. Do not log into another channel to save the terminated channel's videos by re-uploading them there. Appeal in Studio within 1 year, with a maximum of 2 appeals, only when you have a genuine ground. For a copyright termination the route is counter notification or retraction, not the Community Guidelines appeal form. Download your Google data with Takeout, because you cannot download YouTube content after termination.

## Sourcing rules

- Build the channel on your own `[GAME]` gameplay first. Record your own missions, stunts, roleplay, heists and car meets, and talk over them. This is the only source with no streamer takedown risk and the strongest position for monetisation review. Make own gameplay at least 50 percent of the channel.
- Get written permission before you post any other creator clip. Ask in writing, by DM or email, for permission to post clips of their videos on this channel, on which platforms, for how long, with what credit, and whether you may monetise. Keep the message, the date, the sender handle and a screenshot or PDF. A streamer saying clips are fine on stream is not the same as a written yes for your channel. Follow the creator's own clip rules exactly when they publish them. Treat no reply as no.
- Treat a live paid campaign brief as the clearest permission there is. A campaign on a clipping marketplace is written permission with a brief attached. Clip only the stream, segment and dates the brief names, follow its hashtag, disclosure and rules exactly, and stop when the budget ends. Breaking the brief means no pay and no permission.
- Treat creators in three buckets, and re-check the bucket before every clip: **(1) Written permission on file** — clip freely within its conditions. **(2) Campaign-only** — clip only under a live campaign brief naming that stream and segment. **(3) Tolerated in practice** — no blanket permission exists; the creator has not published a clip programme and has not objected publicly, so the usual outcome is a Content ID claim (revenue to the rights holder), not a strike — but a strike remains possible by manual takedown at any time. Tolerance is not permission, and tolerance can be withdrawn at any time. Clip tolerated creators commentary-led only, at low volume, and expect claims and no YPP revenue.
- Never touch any creator who has said do not clip, disabled platform clipping, or issued takedowns. Check the channel About, pinned posts and Discord, and whether Shorts remixing is switched off, before clipping anyone. Never clip a creator to manufacture drama and do not take moments out of context.
- Never touch sports leagues, broadcasters, film and TV rights holders. They strike fast, for seconds of footage. Never clip a segment where the streamer is showing TV, film, sports or another creator video. The streamer tolerance does not cover the underlying rights holder.
- Never touch the game publisher's pre-release or leaked footage, endings, cutscene compilations, in-game TV on its own, or cheats, glitches and money exploits. The publisher lists each as a takedown. Cutscenes are fine only inside a full playthrough or narrated Let's Play. Isolated videos of the game's cinematics will be removed.
- Never post gambling or casino stream segments. YouTube and TikTok restrict gambling content, and casino logos, links or codes can get a clip removed.
- Keep a do-not-clip list and check it before every edit. Keep a source log for every video with the source creator, the source URL, the date, the permission status plus evidence, the music status, the per-clip evidence-test one-liner, and the edit you made. Without it you cannot answer a claimant in the first hour.
- Act on a takedown request within 24 hours, every time. Make the video private or delete it, reply confirming removal, apologise briefly, and do not argue fair use. Log the date, the claimant, the video, the action and the reply. Never re-upload a video a creator asked you to remove, even edited, even on another channel.

**Worked example — GTA VI creator buckets, status snapshot November 2026.** Re-verify every entry before clipping; creators change policy without notice.
- Campaign-only (paid examples on file): IShowSpeed (an Expedia campaign at $1 per 1,000 views covered only one named segment of one named stream); Kai Cenat (a $10,000 pool with a 350,000 approved-view minimum for any share). Outside campaigns both are tolerated in practice, not safe.
- Paid private network, no open sign-up: the N3on/Adin Ross network (reported $1.4M+ paid to ~300 clippers in five weeks, Apr 2026). When you are not in the network, you have no permission. Do not assume access.
- Unverified — get written permission first, do not clip on an assumption: Mythpat, CarryMinati, Typical Gamer, xQc. No public clip policy, programme or written permission was found for any of them in searches at snapshot date. (CarryMinati himself nearly lost his channel in 2016 after 3 copyright strikes from creators he roasted — creators in this ecosystem do file strikes.)
- Never touch: QTCinderella — she stated on 28 May 2026 that she will issue DMCA takedowns for disingenuous or malicious use of her content by clip accounts; in Oct 2026 a user alleged 10 takedowns for 2025 clips. The falsity allegation is not independently established, but the stated intent to DMCA clip accounts is documented.
- Publisher takedown list (Rockstar fan-content policy, verified live 2026-11-23): pre-release/leaked footage, spoilers and endings, edited cutscene combinations, in-game TV in isolation, cheating/glitch/money exploits, unauthorised mods/ports. Note the policy's own scope: it addresses "occasional, non-commercial in-game content use by individual members of the fan community" and says non-commercial means not making money through the footage. A monetised clips channel is, on the face of that text, outside the tolerance it describes. Treat publisher tolerance as no protection for a commercial channel — permission and transformation are still the whole defence.

## Music hygiene

- Treat background music in a source stream as the number one clipper DMCA vector. Labels use Content ID. A recognisable song, even faint in the background, can claim or block the video. This is separate from the streamer permission. The streamer does not own the music.
- Treat in-game music as not copyright-free. In-game radio is licensed third-party tracks, and the original score is also protected. Publisher tolerance for gameplay does not cover the music. Labels claim independently of the publisher.
- Treat the game as having no streamer mode unless the publisher has announced one. Do not assume the streamer muted the music. Verify by listening to each clip.
- Mute, erase or replace any copyrighted music in a clip before upload. Use YouTube Studio Erase song, Trim out segment or Replace song on a claimed video. Use only YouTube Audio Library or other royalty-free tracks whose licence expressly covers YouTube monetisation. Read the terms, because some royalty-free sites do not give YouTube monetisation rights.
- Never add a commercial song as a soundtrack to a compilation. Never leave in-game radio or background stream music in a clip. When a clip's music cannot be removed without killing the moment, do not post that clip.
- Check every upload in Studio, Content, Restrictions before publishing. Upload as Unlisted, wait for the Content ID check, then publish or fix. Keep clips under 60 seconds so a music claim cannot trigger the over-1-minute Shorts block.
- Never dispute a music claim on fair use unless you have a genuine, specific fair-use argument and ideally legal advice. A baseless dispute is the escalation path to a strike. Accept the claim, mute or trim, or delete and re-upload clean.
- Never fix music detection with pitch or speed changes. That is the Spam Policy detection-evasion example and a reused-content failing example for songs.

## Transformation rules

- Add your own voiceover commentary, ranking, analysis or story throughout the video. Set up the moment, explain why it is funny, say what the player did wrong, compare it to other attempts, and build a narrative arc across a compilation. On-screen text must reframe the clip, not just transcribe it.
- Treat captions, emojis, a music track, a speed or pitch change, a reaction face with no voice, an intro or outro slapped on an otherwise untouched clip, or a title that does the commentary while the video does not, as not counting. YouTube states that when your creation does not add new expression, meaning or message to the original, it probably is not fair use.
- Use only as much of each source as the commentary needs. Never use a full segment. Never use the heart of the work as a standalone video. The punchline must sit inside your commentary, not instead of it. There is no safe clip length in YouTube policy or in US fair-use law. YouTube says even a few seconds can be claimed.
- Do not post a clip that replaces the original. Link the original prominently and drive viewers to it. A clip that sends viewers to the original is easier to defend and easier to get permission for than one that competes with it.
- Do not use speed, crop, mirror or filter changes to evade Content ID. YouTube Spam Policy names speeding up audio, heavy filters and cropping to bypass detection as detection evasion, and says it may suspend monetisation or terminate the channel or account. A vertical reframe for legibility is fine. It just does not count as transformation on its own.
- Do not run one template for every video. Vary the structure, the commentary angle and the editing, or YouTube will treat the channel as mass-produced even when each clip is individually defensible.

## Content production workflow per video

- Source the moment. Start from own gameplay, then a live campaign brief, then a tolerated streamer, in that order. Verify the stream is not leaked or pre-release, not a cutscene compilation, not the ending, not in-game TV, not a cheat or glitch video, and not a segment showing TV, film, sports or another creator video.
- Check permission. Confirm written permission on file, or a live campaign brief naming this exact stream and segment, or a documented decision that the use is defensible commentary. Check the do-not-clip list and the creator clip rules. Log the source creator, the source URL, the date and the permission status.
- Run the per-clip evidence test. Write the one-liner: what the clip proves, what your commentary adds. No one-liner, no cut.
- Cut the clip to 59 seconds or shorter. Pick the moment, cut the setup and the payoff, and keep the edit tight. Do not lengthen past 60 seconds.
- Add commentary and narration. Record your own voiceover that ranks, reacts to, explains or tells a story around the clip, throughout the video. Add on-screen text that adds information. Vary the structure from the last video.
- Check the music. Listen to the whole clip. Mute, erase or replace any licensed music, radio or score. Add only YouTube Audio Library music when a bed is needed.
- Apply SEO. Pick one Tier 1 keyword, write the title from a title formula with the keyword first, write the description from the template with the keyword in sentence one, add 5 to 10 tags, add the locked 4 hashtags (plus an optional moment tag), and credit the creator by handle with the original link and timestamp.
- Build the thumbnail. For long-form, use a high-contrast freeze frame of the fail moment, 3 words or fewer, one red arrow or circle only when it points at something real in the frame, and the consistent font and colour. Never use a moment that is not in the video. For Shorts, the first 1 to 2 seconds carry the hook, with big on-screen text in frame 1. Lint title + thumbnail as one pairing before export.
- Run the pre-publish checklist. Confirm the title, the description, the tags, the hashtags, the credits, the music status, the permission log entry, the evidence-test one-liner and the thumbnail all match the video. Confirm the video is honest about what it contains. Confirm the owner has approved the video.
- Upload as Unlisted first. Check Studio, Content, Restrictions for claims. Fix any claim by trimming, muting or replacing before the video goes public. Then publish or schedule. Publish 1 Short per day, 2 per day maximum, spaced 4 to 6 hours apart.
- Verify live after publish. Open the public video, confirm the title, the description, the thumbnail and the first seconds are correct, confirm it is in the right playlist, and post the pre-written comment with the question, then pin it once Advanced features allow. Reply to early comments in the first hour.

## Worked example — launch-week source map (GTA VI, snapshot 19 Nov 2026)

All view counts below are launch-week snapshots from the date shown, not final totals, and not a ranking of who to clip today. Use this section as the shape of a source map: tier the sources by reaction density and VOD length, note language and competition, and re-verify every number before acting on it.

- Tier 1 clip sources (reaction density, long VODs): IShowSpeed, YouTube, English, USA — peak concurrent 372,082; VOD ~39.9M views in the first 15 hours; ~10-hour daily streams; loudest reactions, arrests and fails; number one clip source by volume. Kai Cenat, Twitch + YouTube, English, USA — Twitch peak 122,106; Part 1 VOD ~11.6M views, 11h 35m; marathon format; opening-scene reactions, Lucia ladder fall, police-escape glitch, sleeping and marathon moments. Mythpat + CarryMinati, YouTube, Hindi-English, India — Mythpat peak 125,360 and 12.8M views; CarryMinati peak 83,800–103,500 and 13.8M views, number one in India by views; ~10-hour streams each, with a joint stream; funny Hindi-English commentary and a huge Indian Shorts audience, with less competition from English clip channels. CaseOh, Twitch + YouTube VOD, English, USA — ~97,000–100,000 live observed, peak not verified; one VOD at 1.22M views; meme-dense, short gag moments ideal for ~52 seconds. Typical Gamer / TGG, YouTube, English — peaks 149,968 / 225,106; 9-hour streams, 7–9.1M views; clean story playthrough, free-roam and exploration, very clip-friendly with no heavy story spoilers.
- Tier 2 regional sources (lower English-language competition — clip with subtitles or translated captions; the reaction is universal even when the language is not): Windah Basudara (Indonesian, peak 392,505); alanzoka (Portuguese/Brazil, peak 361,813); Rubius (Spanish, peak 358,695); IlloJuan (Spanish, peak 400,510); HoneyMad (Russian, peak reported 642,053 — corroborated by live snapshots at 568,000–608,000 but absent from the tracker's own top-10 graphic; treat the rank as reported and corroborated, not undisputed); xQc (English, peak 105,106, 23-hour stream); MontanaBlack88 (German, peak 173,953, 100-hour marathon advertised).
- Tier 3, search-driven not reaction-driven: walkthrough channels with no facecam — add your own commentary and text; use only for intro, first mission and first police chase Shorts.
- Viral moments to chase first, with your own commentary on top (no invented in-VOD timestamps — none were found in the sources checked): opening scene, Lucia and Jason fake-couple police stop; Lucia falls off a ladder and Jason dives in after her; streamer arrested stealing a mobility scooter; boat stuck under a bridge and moving erratically; Lucia falls through the ground (collision glitch); police fight with characters passing through solid objects; police escape, falls through the floor; flying car after a collision, truck launched across the map; creator watches a download bar with ~465,000 people; 5-star police chase at the beach; streamer versus trees.
- Avoid clipping nude or strip-club scenes. YouTube sent warnings to several creators over in-game nudity within hours of launch, and one creator had a stream removed by a strike. Credit the original streamer and channel on screen and in the description.
- Chase these search angles for Shorts: opening-scene argument, first arrest and first fail, police chase, free-roam exploration, glitches and flying vehicles, where-is-X, new-features lists, before-you-buy and is-it-worth-it reactions, and non-English creator reactions.
- Competitor picture (snapshot, same date): established clip channels in the niche ranged from ~20,000 subscribers with hundreds of millions of views to ~5M subscribers; one ~5M-subscriber channel had gone inactive, which shows cadence is the moat; a 26M-subscriber crew channel was own-played montages, not a third-party clip channel; a 2.5M-subscriber channel on only 64 videos shows a small number of exceptional compilations can out-earn hundreds of average ones. Views do not equal subscribers.

## Visual generation route

- Generate every visual in your chosen image-generation tool, with its best/pro image model explicitly selected — never assume the default model is the best one. If your tool offers an exact-size mode, use it; if it does not, generate then resize after.
- Never use a tool that cannot produce exact sizes for exact-size work. A video tool or flow that only approximates ratios is a fallback for non-size-critical visuals only, and only when the primary tool is unavailable.
- Use image-editing software only for post-generation work: resize to exact dimensions with high-quality resampling, pad, and compress. A software-built visual never ships as a deliverable. Every chart, timeline, diagram and data graphic is generated in the image tool with the real data in the prompt, never as boxes drawn in an editor.
- Fit outputs to exact dimensions after generation. Native generator sizes are never exact. Pad with the brand background colour bars, never crop, because cropping cuts text.
- Generate the logo, the banner and the master logo with a researched premium brief: one mark only, two colours, flat vector, no gradients, no 3D look, no clutter, no controller, no skull, no flames. The banner keeps mostly empty space, with the mark on one third and the channel name plus subtitle on the other.
- Regenerate any visual that looks like generic AI slop. Make it simpler and flatter, with more empty space. Never accept a cluttered version.
- Word-scan every visual before it ships. Check every word and number against the brief. Regenerate on any defect.
- Every visual goes through the owner approval gate before it goes live. See the channel identity section.

## Red lines, never cross

- Never upload other clips with no permission, no commentary and no music check. That is the exact profile of a channel that gets 3 strikes in 90 days.
- Never write "no copyright infringement intended", "I do not own", or a Section 107 block and believe it protects you. It does not, and it can read as an admission you knew the material was someone else's.
- Never dispute a Content ID claim you cannot defend. A weak dispute can escalate a claim into a strike, and you cannot cancel a submitted dispute.
- Never file a counter notification on a clip you knowingly took without permission. It is sworn, your name, address and phone go to the claimant, and a fraudulent filing can terminate the account.
- Never use a second channel to post during a strike freeze, or to re-upload a removed video. That is circumvention. The Low Tier God case is the textbook example: terminated in Dec 2022 for using a subsidiary clips channel to evade a suspension.
- Never create a new channel after a termination to get around it. The only sanctioned restart is Second Chances after 1 year, and copyright terminations are excluded from it.
- Never post cheating, mod-menu or glitch content, isolated cutscenes, ending or spoiler compilations, in-game TV standalone, or leaked or pre-release footage. The publisher lists each as a takedown.
- Never add commercial music to a clip or as a compilation soundtrack, and never leave in-game radio or background stream music in.
- Never use misleading titles or thumbnails, bulk-upload, or buy engagement. That is a spam termination, not a copyright problem, and it does not need 3 strikes.
- Never re-upload a video a creator asked you to remove, and never argue with a claimant in public. Remove within 24 hours, confirm, and log it.
- Never share the channel login, 2-Step codes or backup codes, and never open sponsor files or sign in through email links. A hijacked channel posts spam or crypto scams and gets terminated for the hacker content.
- Never delete a struck video to make the strike go away, except for a scheduled removal inside its 7 days. Deleting does not remove a strike and ends your chance to appeal that video.

## Documented cases to remember

- xQc, YouTube channel terminated 25–26 Nov 2023, 2.3 million subscribers, over copyright violations on reaction content showing other full videos with little commentary. He said he had several strikes and pending counterclaims that did not kick in in time. Whether or when the channel was restored was not verified in the research. Do not cite a restoration.
- Low Tier God, terminated 21 Dec 2022 for using a subsidiary clips channel to evade a suspension. Both channels were terminated for evading the suspension.
- SSSniperWolf, temporarily demonetised Oct 2023, not terminated, after accusations of freebooting TikTok videos with minimal credit and minimal transformation, then doxxing the critic. YouTube temporarily demonetised the channel.
- QTCinderella, Oct 2026 allegations of 10 takedowns. The claims have not been independently established as false. Do not present this as a proven false-DMCA case.

## Open questions — treat as unverified

- Treat publisher fan-content tolerance for a monetised clips channel as unverified. The Rockstar policy page as read covers non-commercial fan use generally; it does not clearly cover a commercial clips channel. Do not assume the same tolerance for unreleased footage. Pre-release footage is expressly a takedown.
- Treat the reused-content appeal window of 21 days and the reapply window of 90 days as unverified against a live Help page. They are consistent across secondary guides. Check Help 1311392 before relying on them.
- Treat whether xQc's channel was restored after the Nov 2023 termination as unverified.
- Treat the exact Shorts claim-blocking wording for Shorts over 1 minute as RESOLVED in Round 2 — Help answer/15424877 re-read live 23 Nov 2026 still states the block ("will be blocked globally"). The 24 Sep 2026 relaxation claim (a second Help page, reported by postnext.io) could not be confirmed on the main page; treat the two pages as conflicting and stay under 60 seconds where a claim is possible.
- Treat the 5-day revenue-hold rule and the rule that a dispute cannot be cancelled as unverified against a live Help page. They are secondary, citing Help 7000961 and Help 2797454.
- Treat the shared-AdSense mass-termination claim as unverified. It comes from a single secondary source.
- Treat anime and faceless compilation mass-removal numbers as unverified. One secondary guide claims thousands of channels were removed, with no primary source cited.
- Treat search volumes and competition scores for game keywords as not existing. YouTube publishes neither. The tiers in this skill are qualitative. Run the top Tier 1 terms through a keyword tool before locking the month-1 calendar.
- Treat CTR and retention benchmarks, such as 6 to 10 percent CTR and 70 to 80 percent Shorts viewed, as unverified third-party rules of thumb. YouTube publishes no thresholds. Third-party virality scores are triage, not truth.
- Treat whether a separate Google account plus separate device or IP is enough to prevent related-channel detection as unverified. YouTube does not publish its signals. Treat separation as risk reduction, not a guarantee.
- Treat country-specific YPP and AdSense availability and local fair-dealing law as not verified in this skill. Check YPP availability for your country in Studio and take local legal advice before relying on a fair-use defence.
- Treat any creator's clip policy as unverified until you have it in writing from the creator or their management. A direct email or DM is the only way to resolve it.
- Never present any item in this list as confirmed. When you report on one, say it is unverified and say what would verify it.

## Ready-to-use texts

All texts use the reconciled position: neutral, factual attribution plus a removal contact. None of them claims a fair-use licence. Replace every bracket before use.

### Channel About

Copy this text, adapted to your channel. Keep it inside the 1,000-character limit.

```
[CHANNEL NAME] is the home of the best [GAME] moments — the funniest fails, wildest stunts and most unbelievable clips, collected in one place. New Shorts daily.

All clips belong to their original creators and are featured here with commentary and full credit in every video description. If you are a creator featured here and want your clip removed or credited differently, email [REMOVAL_EMAIL] and we will remove it immediately. [GAME] and [GAME FULL TITLE] are trademarks of [PUBLISHER]. This channel is not affiliated with or endorsed by [PUBLISHER].
```

Worked example — GTA VI About (657 characters, inside the limit):

```
[CHANNEL NAME] is the home of the best GTA VI moments — the funniest fails, wildest stunts and most unbelievable clips, collected in one vault. New Shorts daily.

All clips belong to their original creators and are featured here with commentary and full credit in every video description. If you are a creator featured here and want your clip removed or credited differently, email [REMOVAL_EMAIL] and we will remove it immediately. GTA VI and Grand Theft Auto are trademarks of Rockstar Games / Take-Two Interactive. This channel is not affiliated with or endorsed by Rockstar Games.
```

### Shorts description template

Fill the brackets per video. Keep the keyword in sentence one. Credit the creator by handle in every description. Use one playlist link only. Shorts description URLs are NOT clickable since 31 Aug 2023 — the playlist link renders as plain text; the click path is the Related Video link set in Studio. Do not build the CTA around the description link. This template applies to future videos only — do not retro-edit the title or description of an already-published or scheduled video.

```
[One-sentence hook naming the exact moment and the primary keyword.]
The funniest [GAME] [fails / stunts / wins] — [one line describing what happens in this clip]. Credit: @[creator handle].
[SUBSCRIBE_LINE]
Full compilation: [playlist link]
[HASHTAG_LINE] #[MomentKeyword]
```

### Per-video credit block, short form for Shorts

Use this in every Shorts description, under the template text above.

```
Credit: [Creator Name] — [original video/stream link]. All rights belong to the original creator. Removal requests: [REMOVAL_EMAIL]
```

### Per-video description, long form

Fill in for each video. State what you added in 1 to 2 lines. That statement is the only part that goes to transformation.

```
[Title of the moment] — commentary by [CHANNEL NAME].

Original creator: [Creator name] — original video: [full URL]
Additional clips: [Creator name — URL] (repeat per clip)

What we added: [1–2 lines — for example "We ranked these five stunt fails, explained what went wrong in each attempt, and compared them to the same stunt in …"]

All rights in the original footage belong to the original creators and to [PUBLISHER]. If you are a creator featured here and want your clip removed, email [REMOVAL_EMAIL] and we will remove this video within 24 hours.
```

### Permission request, DM or email to a streamer

Keep the reply, with a screenshot, the date and the handle. When they say yes with conditions, write the conditions into the allow-list and follow them.

```
Hi [name] — I run [CHANNEL NAME], a small [GAME] clips channel on YouTube ([CHANNEL_HANDLE]). I would like permission to post short clips from your [streams/videos] with my own voiceover commentary, full credit to you and a link to your original video/stream in every description.

I would only use short moments (not full segments), I would not use clips you ask me not to, and I would remove any clip within 24 hours if you ask. I will not add commercial music over your clips.

Would you be happy for me to do that? If yes, are there any rules (platforms, which videos, credit format, monetisation) you would like me to follow? I am happy to share revenue / link your channel in return if that helps.

Thank you — [your name, channel link, removal email]
```

### Retraction request, email to a claimant after a strike

Send within hours. Do the removal before sending. Do not argue fair use in this email. Do not threaten a counter notification. Send one polite email, then wait. Do not spam the claimant.

```
Subject: Request for retraction — copyright strike on [video title / video URL]

Hello [claimant name],

I am the owner of the YouTube channel [CHANNEL NAME]. You filed a copyright removal request for my video "[title]" ([URL]), and my channel has received a copyright strike.

I apologise — I should not have used your material in that way. The video has been made private / deleted [choose one — do it before sending].

I have removed the material and I will not re-upload it. I have also reviewed my other uploads and [removed / made private] any other videos using your material.

Would you be willing to retract the copyright removal request? I understand this is at your discretion. If you retract it, the strike will be removed from my channel.

Thank you for considering this, and again I apologise for the use.

[Full name, channel name + URL, contact email, phone if you are comfortable sharing it]
```

### Content ID dispute text

Use only when you have a real ground. Adapt it, do not copy it blindly. Pick one true ground and delete the others.

```
I dispute this claim because [choose ONE true ground and delete the others]:
— I have written permission from [creator/rights holder] to use this material on YouTube, granted on [date] by [name/handle]. A copy is attached / available on request.
— This material is my own original gameplay / recording, not the claimant's file. The match is a false positive because [specific reason — for example same game, different playthrough].
— This use is fair use for commentary/criticism: I use only [X seconds] of the original, I add my own voiceover commentary throughout that criticises/analyses [specific point], and the clip does not substitute for the original, which is linked in the description.

I understand that if this dispute is rejected I may appeal, and that the claimant may submit a copyright removal request.
```

When none of those sentences is true, do not dispute. Trim, mute, replace, or accept the claim.

## Available connectors

- Email (e.g. Gmail) for permission requests, retraction requests and the removal inbox. Answer the removal inbox within 24 hours.
- Cloud storage (e.g. Google Drive) for clip storage, exports and permission evidence. Keep every original project file, export, permission email and thumbnail outside YouTube from day one.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Websites

- [YouTube Studio](https://studio.youtube.com/) for uploads, Content ID checks, strikes, playlists and analytics. Verify the channel before every action. Upload as Unlisted first and check Content, Restrictions before publishing.
- [YouTube Help — channel monetization policies (reused content)](https://support.google.com/youtube/answer/1311392) — the primary source for the reused-content and inauthentic-content rules in this skill. Re-read it before any YPP application.
- [Rockstar fan-content policy](https://support.rockstargames.com/articles/7bNaeoMFTV0iUDGhStTXvz/policy-on-posting-copyrighted-rockstar-games-material) for the publisher takedown list. Licensing questions go to copyright@take2games.com.
- Clipping-campaign marketplaces (e.g. Vyro, Content Rewards) for live paid clipping campaigns. Check each week for a campaign in your game before clipping a tolerated streamer for pay.

## Alternatives for better results

- Record your own gameplay with your own commentary as the channel base. It is the only source with no streamer takedown risk and the strongest monetisation position.
- Check clipping-campaign marketplaces each week for a live campaign in your game before clipping a tolerated streamer. Campaign pay is the durable income for this material, not YPP ads.
- Diversify the source across own gameplay, multiple creators and campaign clips, so no single takedown or policy change kills the channel.
- For a general original-content channel, use the `youtube-operator` skill. For Shorts-specific diagnosis (zero views, feed reach), use a Shorts diagnostics skill. This skill stays the clips-channel specialist: permission, transformation, music, strikes.
