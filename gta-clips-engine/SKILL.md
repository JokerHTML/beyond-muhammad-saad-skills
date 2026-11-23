---
name: gta-clips-engine
description: "Turn long game streams into ready-to-post vertical Shorts — free, local, no API keys: find the moment, score it, render it 1080x1920 with captions and a full posting pack. For anyone clipping streams they have permission to use."
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
updated: 2026-11-23
---

# Stream-Clipping Engine — Build and Run a Free ($0) Local Clipper

Turn a long game stream into ready-to-post vertical Shorts on your own
computer, for $0, with no API keys, no subscriptions and no cloud
credits: discover the biggest streams, download audio only, find the
moments with loudness + chat + face signals, score them, render
1080×1920 with karaoke captions, and emit a self-checked posting pack
(title, description, tags, thumbnail spec, first comment).

Use this skill when building, running, or fixing any part of such an
engine — or when deciding whether to build one instead of paying for
Motion Mania Pro, OpusClip, or a similar tool. It is the build manual
and the operating manual in one file.

**Worked example used throughout:** GTA VI. Every game-specific term,
number and source in this skill is a dated worked example of the
method, not a universal fact. Swap in your game and re-run the
verification steps — never carry the example's keywords, hashtags or
view counts into another game.

**What this skill is not:** it is not an upload/scheduling tool, not a
phone app, and not a promise that clips earn money. The engine writes
files and packs; upload is a separate, human step. See §10 for the
full honest list.

## 0. Configure first — fill every placeholder before any clip

Nothing in this skill works until these are set. Keep them in one
config file you can re-read in one glance.

- `[GAME]` — the one game this engine covers, e.g. `GTA VI`.
- `[GAME_TITLE_SPELLING]` — the spelling every title uses, e.g.
  `GTA VI` (never `GTA 6` in titles). Tags and descriptions carry both
  spellings for search; titles carry one, as a brand decision.
- `[CLEARED_STREAMERS]` — streamers with a clipping program or
  written permission. Clip ONLY these. Never clip a streamer on
  rumour, on "everyone clips them", or on a deleted permission.
- `[NEVER_STREAMERS]` — streamers who must never be clipped, even if
  a moment is perfect. Check it before every batch.
- `[PERMISSION_STREAMERS]` — streamers who need written permission
  first. No permission on file = no clip.
- `[CONTACT_EMAIL]` — a dedicated public contact email for removal
  requests. Never reuse another channel's address.
- `[SUBSCRIBE_LINE]` — the one locked subscribe sentence used in every
  description, e.g. `Subscribe for a new GTA VI clip every day.`
- `[HASHTAG_LINE]` — the locked hashtag line, e.g.
  `#[Game] #[GameAlt] #GamingNews #[Streamer] #[Moment]` (≤6 total).
- `[CHANNEL_TAGS]` — the 2–3 channel-name tags that are the one
  intentional repeat on every video, e.g. `yourchannel, your channel
  name, yc`. Content tags are fresh every time; channel tags repeat.
- `[PUBLISH_CADENCE]` — e.g. 1 Short/day at a fixed time. No batch
  dumps.
- `[FIRST_COMMENT_DELAY]` — post the first comment 1 hour after the
  video goes public, never 5 minutes after.
- `[ENGINE_ROOT]` — where the engine code lives, e.g.
  `~/engine/stream-clipper/`.
- `[ENGINE_PKG]` — the engine's Python package name, e.g.
  `streamclipper` (commands run as `python -m [ENGINE_PKG].cli`).
- `[VENV_PYTHON]` — the Python with the engine's dependencies, e.g.
  `~/.beyondgtaclips/venv/bin/python` (faster-whisper, OpenCV,
  ONNX Runtime).
- `[WORK_DIR]` — scratch inside the engine root, e.g.
  `[ENGINE_ROOT]/work/`. Never `/tmp` for audio/video (512 MB tmpfs
  fills and kills the job).

## 1. Hard constraints (never break these)

- **$0 only.** No API keys, no subscriptions, no paid services, no
  cloud credits. Local-first, CPU-friendly (the reference build ran
  on 1.5 shared CPUs, 6 GB RAM).
- **NEVER publish / upload / schedule anything; NEVER touch the live
  channel.** The engine writes files + packs. Upload is the owner's
  step, or a separate publish task on the owner's word.
- **NEVER delete anything.** The engine itself deletes nothing.
- **Cleared streamers ONLY** (`[CLEARED_STREAMERS]`). Never clip
  anyone on `[NEVER_STREAMERS]`.
- **No fabrication anywhere.** No invented moments, numbers, quotes,
  views, or earnings — in code, packs, docs, or comparisons.
- **Permission ≠ monetisation.** A clipping program or written
  permission lets you clip; it does not promise YouTube Partner
  Program acceptance. YouTube's reused-content policy can still flag
  compilations or clips "edited together with little or no narrative"
  even with permission — the Oct 1 2026 Shorts originality update
  deprioritises re-uploaded clips in the feed even with permission +
  credit. Transformation must be in the video (layout, hook,
  subtitles, curation, and — for compilations — your own voiceover /
  narration + a story structure), not in the credit line.

## 2. Pipeline order (run in this order; each stage's output is the next stage's input)

| # | Stage | Reference module | What it does |
|---|---|---|---|
| 1 | **Discover** | `discovery.py` — `discover()`, `search_streams()`, `dedupe_and_rank()` | yt-dlp search (`ytsearch:`), no API key; rank by views/hour; exclude re-uploads/compilations; cleared-streamer allowlist enforced (`is_cleared()`, `classify_streamer()`) |
| 2 | **Audio-only download** | `audio.py` — `download_audio()`, `extract_window()` | yt-dlp `-f ba/b`, ~220 MB per 4 h. NEVER full video for analysis |
| 3 | **Triage signals** | `loudness.py` — `measure_series()`, `find_spikes()`, `confirm_spike()`; `chat.py` — `analyse_chat()`, `detect_spikes()`, `spikes_to_windows()`; `face.py` — `FaceDetector`, `sample_faces()` | Cheap signals FIRST (loudness + chat rate), expensive stages only on candidate windows. Loudness: ffmpeg `ebur128` (M/S series), spike = short-term LUFS ≥9 LU above trailing 60 s median, confirmed by `astats` peak. Chat: TwitchDownloaderCLI chat JSON / `chat-downloader` / yt-dlp `live_chat`; rolling median+MAD, z ≥ 3, merge <30 s, window −20 s / +10 s. Face: OpenCV YuNet, 1 fps sampling |
| 4 | **Transcribe windows only** | `transcribe.py` — `transcribe_window()` | faster-whisper `tiny`/`base` int8, `word_timestamps=True`, `vad_filter=True`. **NEVER a whole VOD — 30–90 s candidate windows only.** Word times drift ±200 ms: fine for captions/hooks, not frame-accurate cuts |
| 5 | **Score + pick** | `scoring.py` — `signal_score()`, `score_purple()`, `estimate_purple()`, `picky_filter()`, `pick_batch()`, `score_candidate()` | Deterministic weighted score (loudness + chat + transcript keywords + emotion + most-replayed) as the base; deterministic score is the ONLY judge in v1 — the Ollama LLM judge is a Phase-2 design, not built (see §5). Keep ~1/3 (Motion Mania keeps 6/18; gta6-clipper keeps 3/39). See §5 |
| 6 | **Purple gate** | `scoring.py` — `purple_verdict()`, `novelty_check()` | Purple Score N(0–3)+V(0–3)+M(0–2)+P(0–2) = /10. **Ship threshold 7/10. P=0 = automatic fail.** Novelty check = search YouTube for the beat + check your own catalog — a seen beat is not purple |
| 7 | **Render** | `render.py` — `house_filtergraph()`, `house_pass_cmd()`, `download_section_cmd()`; `proedit.py` | Segment-only video download (`--download-sections`), house layout (facecam top / gameplay below, 65/35 default), ASS karaoke captions (≤4 words/line, ≤18 chars), 1080×1920, −14 LUFS. Pro-edit: jump cuts, zoom punch, grade (locked chain), synthesised/CC0 SFX, meme-fit rating (drop <7). See §6 |
| 8 | **Storyline (optional)** | `storyline.py` — `build_story()`, `validate_arc()` | 2–5 beats, setup → turn → payoff, streamer-centric. If no arc scores ≥7, ship singles only — never force a story |
| 9 | **Posting pack** | `pack.py` — `generate_pack()`, `check_pack()` | Title formula, Template A description (13 gates), 10 fresh tags, thumbnail spec, first comment at publish +60 min. Self-check FAILS the pack on any gate. See §7 |
| 10 | **Human review → manual upload** | — | Watch every clip before it goes out. Upload on `[PUBLISH_CADENCE]`. First comment at publish +60 min, never +5 min. Read back title/description/tags/playlist/schedule from the details page, never the list view |

**Shared contract:** every stage passes the candidate JSON defined in
`contract.py` (`new_candidate()` / `validate_candidate()`):
`{id, streamer, vod_url, vod_id, start_s, end_s, transcript,
signals{ loudness_db, loudness_z, chat_spike_z, chat_rate,
emotion{label, score} }, purple{ N, V, M, P, total }, score, hook,
title_idea}`. Never invent a second shape — extend this one.

**CPU rules (binding):** run the pipeline as a strict sequence
(triage → score → transcribe window → render), one heavy stage at a
time. Never run STT + emotion + ffmpeg encode concurrently on a weak
machine. Never transcribe a whole VOD. Never download full video for
analysis.

## 3. Commands (reference implementation)

```bash
cd [ENGINE_ROOT]
VENV=[VENV_PYTHON]

# Discover today's biggest [GAME] streams (48 h window, top 10)
PYTHONPATH=src $VENV -m [ENGINE_PKG].cli discover --within 48h --count 10 --pretty

# Audio-only download (whole VOD audio, or one section)
PYTHONPATH=src $VENV -m [ENGINE_PKG].cli audio <url> --out-dir work
PYTHONPATH=src $VENV -m [ENGINE_PKG].cli audio <url> --start 5884 --end 5925

# Loudness spikes on an audio file (threshold 9 LU over trailing median)
PYTHONPATH=src $VENV -m [ENGINE_PKG].cli loudness work/audio.wav --threshold 9.0

# Transcribe ONE 30–90 s window only
PYTHONPATH=src $VENV -m [ENGINE_PKG].cli transcribe work/audio.wav --start 5884 --end 5925 --model base

# Posting pack from a scored candidate JSON (fails loudly on any gate)
PYTHONPATH=src $VENV -m [ENGINE_PKG].pack candidate.json --out pack.json
#  -> writes pack.json + pack.md (copy-paste rendering)

# Tests (stdlib unittest only)
PYTHONPATH=src $VENV -m unittest discover -s tests -v
```

## 4. Triage signals — cheap first, expensive only on candidates

| Signal | How it is measured | Rule |
|---|---|---|
| Loudness spike | ffmpeg `ebur128` M/S series; `find_spikes()` + `confirm_spike()` (`astats` peak) | Short-term LUFS ≥9 LU above the video's trailing 60 s median S, AND momentary peaks ≥6 LU above median in the same window. Baseline is PER VIDEO (and per channel over time) — never a fixed LUFS number |
| Chat spike | `chat.py` `detect_spikes()` (rolling median + MAD, 10 s bins) | z ≥ 3 AND count ≥ 2× rolling median; merge spikes <30 s apart; window −20 s / +10 s around the peak. Emote/keyword bursts (W, LOL, OMG, CLIP) are a second, independent signal |
| Transcript keywords | `keyword_hits()` — hype words, laughter markers, scream words in the window transcript | Supports the score; never the sole trigger (a loud transcript with no loudness/chat/emotion agreement is a talky segment, not a moment) |
| Face emotion | YuNet detection (1 fps) + emotion model on the largest face crop, smoothed over 1 s windows | Weak signal only (see §5.3). Labels a clip funny / scream / shock / rage / hype and steers the edit — never a standalone pick |
| Most-replayed | Public heatmap data where available (YouTube VODs) | Complement, not a requirement — most VODs will not have it |

**Agreement rule:** a clip needs at least TWO agreeing signals (e.g.
loudness + chat, or emotion + loudness) before it is promoted to
scoring. One signal alone is noise until proven otherwise.

**Per-channel baselines:** chat and loudness are always scored against
the channel's/video's OWN recent normal (Motion Mania's "live-aware"
design, verified on its Features page) — a 50-msg/10 s spike is huge
for a 200-viewer streamer and noise for a 60M-subscriber one. Never
use a global threshold.

**Known gaps:** Kick has no mature chat downloader — Kick candidates
score on loudness + transcript + face only. `chat-downloader` is stale
on some VODs (it fails on some VODs yt-dlp reads fine) — the yt-dlp
`live_chat` fallback is unbounded for VODs >1 h and is skipped for
time-bounded requests. Twitch chat download needs a real VOD id to
verify end to end.

## 5. Scoring — deterministic score + Purple gate (the judge is NOT in v1)

### 5.1 Layer 1 — deterministic weighted score (always on, no model)

Module: `scoring.py` — `signal_score()`, `score_candidate()`.
Weights: loudness 0.25 + chat 0.30 + emotion 0.15 + keywords 0.30,
fused to 0–100. Inputs come from the triage stages on the shared
candidate contract. Missing signals score 0 for that component and are
listed in `missing_signals`, so a low score is never mistaken for a
measured low score.

### 5.2 Layer 2 — LLM judge: Phase-2 design, NOT in v1

Do not present an LLM judge as part of this engine. The reference
build is **deterministic only — no LLM, no network, no API keys** in
scoring. The designed second layer is an Ollama Qwen judge (Qwen3 /
Qwen 3.5, 9B-class at 16 GB RAM, 27B-class at 32 GB+) reading
transcript chunks of the shortlisted windows only — exactly as
gta6-clipper does (12-min chunks, harsh filter, 7+ threshold) — with
the deterministic score holding a VETO over any judge pick with no
signal support. That judge is **unbenchmarked on a 6 GB machine** and
was not run in the reference build; shortlist size and chunk length
need a measured run before it is trusted. Never present a Qwen score
as a Claude score, and never run a judge on a whole VOD.

### 5.3 Face emotion — settled model, weak signal

The emotion model choice is **settled in the reference build**:
HSEmotion / EmotiEffLib `enet_b0_8_best_vgaf` (16 MB ONNX) as primary,
ONNX FER+ `emotion-ferplus-8` fp32 (35 MB) as fallback — the 19 MB
int8 file's upstream URL 404'd on 2026-11-23, so fp32 is bundled
instead. The HSEmotion licence was verified by reading the upstream
LICENSE file in full on 2026-11-23: **Apache License 2.0**
(permissive, including commercial use, with attribution). Both model
files ship in the engine `models/` directory.

Whichever model is used: emotion-from-face is a WEAK signal.
In-the-wild accuracy is ~61–66% (AffectNet-8 61.3%); disgust/fear are
under-predicted; face labels are not a reliable read of how someone
feels. Sample at 1–2 fps, smooth over 1 s windows, never trust a
single frame, never use it as a standalone pick signal, never use it
for decisions about a person. Scores below 0.35 map to "neutral".

### 5.4 Purple Score — the remarkability gate (after scoring)

Module: `scoring.py` — `score_purple()`, `estimate_purple()`,
`purple_verdict()`, `novelty_check()`. Rubric: N (0–3 novelty) + V
(0–3 expectation violation) + M (0–2 memorability) + P (0–2 payoff
truth) = /10. Score the moment + title TOGETHER, not the moment alone.

| Total | Meaning | Action |
|---|---|---|
| 0–2 | Seen it a hundred times | Do not build |
| 3–4 | Familiar with a twist | Do not build as-is |
| 5–6 | Unusual, not unforgettable | Rework the angle first; ship only flagged as a known normal cow if the slot must be filled |
| **7–8** | **Purple — ship standard** | Build |
| 9–10 | Unmistakable | Build; expect 1–2 per batch of 10, not 10 per batch |

**Hard rules:** ship threshold **7/10**. **P=0 = automatic fail**
(the promised beat is absent or exaggerated — clickbait, not a purple
cow). Never lower the threshold to clear a queue. `novelty_check()`
runs Test A: search YouTube for the beat's keywords + check your own
catalog (your shipped-beats file / SEO packages) — if the exact beat
is already out there, by you or anyone, it is not purple. A shipped
beat forces N=0.

### 5.5 Pickiness — how many survive

`picky_filter()` / `pick_batch()` keep ~1/3 of found moments.
Reference keep rates: Motion Mania 18 found → 6 kept (~33%);
gta6-clipper 39 possible → 3 kept. A pipeline that keeps everything
is not picking — it is dumping. If your batch keeps >50%, the scoring
is broken, not the batch.

## 6. Render + pro-edit — one ffmpeg invocation per final clip

Order: `trim → scale/crop house layout → punch/zoom (hook beat only)
→ ASS burn-in → libx264`. Never chain MoviePy → ffmpeg → ffmpeg;
every extra encode generation costs quality and CPU time on a weak
machine.

### 6.1 Inputs (gather, don't guess)

- Scored candidate JSON (shared contract) with `start_s` / `end_s`,
  `hook`, `title_idea`, transcript with word timestamps.
- Source VOD URL. Download ONLY the minutes that become clips:
  `render.py` `download_section_cmd()` / `download_segment()` —
  `yt-dlp --download-sections "*start-end"`. Audio + video in ONE
  download command silently truncates audio — download audio alone +
  video alone, then mux. NEVER full VODs.
- Facecam geometry: `render.py` `house_filtergraph()` takes
  `cam, game_x` (+ a `no_facecam` variant — clips with no facecam use
  a wide gameplay top band, never a black band).

### 6.2 House layout (the default)

- **Canvas:** 1080×1920, 60 fps, vertical. Facecam top / gameplay
  below (65/35 split as the default game layout).
- **Hook band:** middle, the moment in words (hook text), on screen
  from frame 1. First frame = facecam reaction + hook text — it IS the
  thumbnail in the feed (Shorts use AUTO thumbnails until phone
  verification).
- **Open on the violation, not the setup:** first frame shows the
  impossible thing already happening. No logo, no establishing shot,
  no "welcome back".
- **Safe zones (1080×1920):** keep hook text/captions inside
  y 240–1540, x 100–940 (top = platform nav, bottom = username/sound/
  CTA, right ~140 px = action buttons).
- **Subtitles:** burned in, transcript-checked. Subtitle style: Shorts
  house style (red, clean, ≤32 chars/line).
- **Other layouts** (Motion Mania set — implement as presets, data not
  code): split, stack, picture-in-picture, duo, face-following
  full-frame, fit (blurred background), speaker focus, smart auto.
  Templates live in `presets.py` (`list_presets()` / `load_preset()`,
  validated by `validate_preset()`). Five presets ship as data:
  house, stack, bubble, cinematic, breaking-news. One consistent look
  per page.

### 6.3 Captions — ASS karaoke (not SRT)

- Source: faster-whisper word timestamps → `.ass` (PlayResX 1080,
  PlayResY 1920). `render.py` `words_to_srt()` / `parse_srt()` /
  `validate_srt()` handle the SRT side; the `.ass` is render-only and
  the `.srt` is still emitted separately for YouTube upload.
- **VTT captions are the subtitle source of truth** where the platform
  provides them — Whisper words are used only when VTT is absent, and
  a 2.5 s silence gap always starts a new subtitle event (max event
  7 s). Whisper hallucination loops are detected and discarded.
- Grouping: ≤4 words/line, ≤18 chars; 3 words/group, break after
  0.7 s silence.
- Style: bold, white fill, black outline, centred low-third; word
  highlight via ASS `\kf` karaoke tags; punchline words get per-word
  colour + size override.
- `render.py` `render_hookband()` draws the hook band with PIL (hook
  text is drawn, never model-rendered).

### 6.4 Final encode (Shorts)

```
-c:v libx264 -preset slow -crf 19 -pix_fmt yuv420p -profile:v high -level 4.1
-c:a aac -b:a 192k -ar 48000 -movflags +faststart out.mp4
```

Draft/preview: `-preset veryfast -crf 23`. Never ship a draft preset
as final. Audio: **−14 LUFS** at export (`proedit.py`
`loudnorm_filter()` / `loudnorm_measure_cmd()`; measure with
`ebur128`, never with `loudnorm input_i` — tail double-count bug in
ffmpeg ≤8.1.1).

### 6.5 Pro-edit effects — FFmpeg filtergraph is the effects engine

Module: `proedit.py`. Every effect is an FFmpeg filter or ASS
override; no $0 library bundles them. Spec = Motion Mania's Pro Edit
table (their Features page, verified 2026-11-23).

| Effect | Implementation | Notes |
|---|---|---|
| Jump cuts (silence trim) | `detect_silences()` + `jump_cut_plan()` + `jump_cut_trim_cmds()`; `silenceremove_filter()` | Silences >~1 s trimmed to a breath (0.25 s). Frame-accurate cuts re-encode the segment — never `-c copy` across a non-keyframe |
| Zoom punch / push-in / shake | `zoom_punch_filter()` (static punch-in, cheapest), `push_in_filter()` (slow Ken Burns), `shake_filter()` | Punch/zoom on the HOOK BEAT only, not the whole clip |
| Grade | `grade_filter()` — the ONE locked encode-time chain (deband → grain → S-curve 0.94 shoulder → saturation 1.00); `grade_encode_cmd()`; `build_hald_lut_cmd()` / `apply_hald_lut_cmd()` | Freeze the chain into a versioned Hald LUT; Rec.709 limited-range with all colour tags; numeric signalstats QC gate every reel |
| Punch captions | `punch_caption_ass()` | 1–3 words, per-word colour, punchline large + quoted |
| Sound design | `synth_sfx_cmd()` / `mix_sfx_cmd()` + `check_sfx_license()` | SFX synthesised in-app (FFmpeg `sine`/`anoisesrc` envelopes) or bundled CC0 — never scraped from a paid library. Ship with a local, pre-cleared SFX pack: licence text + source URL recorded per file. Primary music sources: Pixabay + YouTube Audio Library. Never fetch music at render time |
| Meme moment | `meme_ending()` / `meme_overlay_filter()` | ONE meme, only on a clear fit; fit-rating 0–10, drop <7 (Motion Mania's rule). No free rival implements this — it is a differentiator, and the easiest effect to get wrong: a weak match is dropped, never shipped |
| Emoji pop / title pop / beat flash | ASS/drawtext timed overlays; flash = `eq` brightness pulse on loudest hits | — |
| Cut to the speaker | NOT implemented in v1 | No $0 reference implementation. WhisperX diarization needs a HF token (gated model) — do NOT use. Phase-2 alternative: mouth-movement proxy (face-box + audio energy per face region) |
| Motion blur on cuts | Partial — `tmix` / `minterpolate` (limited) | Stretch goal, not a v1 promise |
| Fix Blur (AI-sharpened facecams) | NOT in v1 — ffmpeg `unsharp` only | True AI upscaling is not $0-local at quality. Do not promise it |

### 6.6 Verification (gate before the pack is built)

- [ ] ffprobe PASS: 1080×1920, 60 fps, ≤3 min (a Short).
- [ ] First frame = facecam reaction + hook text, not a black frame
      or a menu screen. Muted 2-second test at thumb distance: the
      violation is visible in those 2 seconds.
- [ ] Subtitles burned in and transcript-checked, ≤32 chars/line.
- [ ] Hook text spelled correctly, no cut-off text, nothing in the
      duration-stamp corner.
- [ ] Audio −14 LUFS; music pre-screen done (MODERATE flags get a
      listen-check before upload).
- [ ] No-facecam clips use the documented no-facecam variant (wide
      gameplay top band), never a black band.

### 6.7 What NOT to do

- Do NOT use MoviePy as the renderer (documented OOM / decoder-leak
  risk on weak CPUs — prototyping only, and only to compose PIL text
  PNGs handed to ffmpeg).
- Do NOT use OpenCV `VideoWriter` for the final encode (no audio
  muxing, no subtitle rendering, no x264 tuning).
- Do NOT use `/tmp` for video scratch (512 MB tmpfs — it fills and
  kills the job). Engine `[WORK_DIR]` on the workspace disk, clean up
  after.
- Do NOT introduce essentia (AGPL) or any AGPL dependency into the
  engine. Do NOT use SCRFD/InsightFace (non-commercial licence).
- Do NOT re-cut the whole queue on one study (e.g. a ≤30 s length
  band is worth ONE test cut, judged at 72 h).
- A file being created does not mean it is correct — ffprobe + watch
  the render before it goes to the pack stage.

## 7. Posting pack — locked rules (`pack.py` enforces all of these)

- **Title:** `[GAME_TITLE_SPELLING]` (never the alternate spelling) ·
  40–60 chars · streamer named · statement, not question · no `!!!`,
  no `…`, no hashtag, no emoji · Formula P (violation first) or
  F1–F6, rotated, never the same formula twice in a row.
  Title formulas (gaming Shorts, 40–60 chars is the measured sweet
  spot — Returbe, 63,480 videos, Nov 2026): moment + reaction;
  number + stakes; "has no idea" gap (max 1 in 5); "why" + fact;
  absolute word ("never" / "nobody"); quoted word actually said in
  the clip (transcript-verified).
- **Description (Template A):** L1 80–120 (streamer + game + moment +
  where, one sentence) · L2 60–100 (supporting detail, different
  words, transcript-verified where quoted) · credit on its own line ·
  locked `[SUBSCRIBE_LINE]` · disclaimer block +
  `Contact: [CONTACT_EMAIL]` · hashtag line `[HASHTAG_LINE]` (≤6
  total). ONLY the clip's streamer is named anywhere (game characters
  are not streamers). L1/L2 fresh per video, checked against your
  shipped catalog.
- **Tags:** exactly 10 (7 content + 3 channel tags last —
  `[CHANNEL_TAGS]`, the one intentional repeat) · both spellings of
  the game name · content tags fresh — checked against your shipped
  tags. Before each upload, search the most-searched/viral tags for
  the topic and use them; never repeat a video's content tags.
- **Thumbnail:** spec only — hook line ≤5 words from the clip's actual
  moment, 1080×1920, deterministic PIL pipeline. Never model-render
  text. Shorts use AUTO thumbnails until phone verification — the
  first frame IS the thumbnail, so the render must open on the
  violation.
- **First comment:** a specific question the clip raises, post at
  publish +60 min — never +5 min. No link, no pitch.
- **Playlist:** the clip goes into the playlist of the streamer whose
  video it is — never another streamer's playlist, never a generic
  playlist when a streamer playlist exists.

## 8. Gates — a failed gate stops the publish

1. Cleared streamer only (discovery + pack both enforce).
2. Purple total ≥7/10 AND P ≥ 1 (P=0 = automatic fail, no exceptions).
3. Title gates (§7) + description 13 gates + viral-SEO 10 gates —
   `pack.py: check_pack()` runs all of them; `generate_pack()` raises
   `PackError` instead of returning a bad pack.
4. Music pre-screen: MODERATE flags need a listen-check before upload.
5. Human watch-through: every clip watched before it goes out; a
   description error found after publish is edited IN PLACE — never
   delete and re-upload to fix copy.
6. `[PUBLISH_CADENCE]`. No batch dumps.

## 9. How it compares — honest, dated, re-check before quoting

Prices below were read live from motionmania.app/pricing on
2026-11-23 (crawled 11:24 UTC): Free $0 forever, 10 clips/day, clips
up to 2 min, 1 live stream, 13 built-in SFX, merge 2–6 clips, offline
titles, 1080×1920 MP4 no watermark. Pro $24.99/mo (Black Friday
$14.99/mo, locked while subscribed; deal ends ~15 days from Nov 23):
unlimited clips, up to 3 live streams, Pro Edit, Storyline, phone app,
paid clipping campaigns with rules built in, Fix Blur, 5 Pro looks,
Smart Titles + AI rating, auto-upload to YouTube Shorts and TikTok
**coming soon** (platform reviews pending). Prices change — re-fetch
the pricing page before quoting any figure in public copy.

| Feature | This engine v1 | Motion Mania Free | Motion Mania Pro | gta6-clipper | beyondgtaclips |
|---|---|---|---|---|---|
| Free ($0) | ✓ | ✓ ($0 forever) | ✗ ($24.99/mo) | ✓ (skill + engine free; AI via $20/mo Claude OR free Ollama/Qwen) | ◐ ($0, no API keys — but good picks ride your existing Claude/ChatGPT subscription) |
| No watermark / no daily cap | ✓ / ✓ | ✓ / ✗ (10 clips/day) | ✓ / ✓ (unlimited) | ✓ / ✓ | ✓ / ✓ |
| Local / runs on your computer | ✓ (Linux-first; Python runs on macOS/Windows, no packaged app yet) | ✓ (Mac + Windows) | ✓ (Mac + Windows) | ✓ (Mac-only main repo; separate Windows fork exists) | ✓ (Mac + Windows) |
| Live-stream clipping (while live) | ◐ (design only — streamlink rolling buffer; NOT run end-to-end; v2) | ✓ | ✓ | ◐ (live skill exists per README; the video transcript makes no live claim — sources conflict) | ✗ (explicitly "not yet") |
| VOD / replay clipping | ✓ | ✓ | ✓ | ✓ | ✓ |
| Auto-find today's biggest streams | ✓ | ✗ (not stated) | ✗ (not stated) | ✓ | ✓ |
| Chat-spike / loudness detection | ✓ (z ≥ 3; ≥9 LU) | ✓ | ✓ | ✓ | ✓ |
| Face / emotion detection | ✓ (YuNet + HSEmotion, settled — §5.3) | ✓ | ✓ | ✗ | ✗ (face used in layout only) |
| Transcript + AI scoring | ◐ (deterministic score + Purple gate; LLM judge NOT in v1 — §5.2) | ✗ (not described) | ✗ (not described) | ✓ (12-min chunks, per-moment score, harsh filter) | ✓ (AI picks + hooks; no score stated) |
| Pickiness (found → kept) | ✓ (~1/3 keep) | ✓ (18 → 6, ~33%) | ✓ (AI rating skips weak moments) | ✓ (39 → 3) | ✗ (not stated) |
| Purple Score / remarkability gate (≥7/10, P=0 fails) | ✓ (enforced in scoring + pack) | ✗ | ✗ | ✗ | ✗ |
| Permission allowlist enforced | ✓ (allowlist in discovery + pack) | ✗ | ✗ | ✗ (honor note only) | ✗ (honor-based) |
| Uniqueness / duplicate check | ✓ (novelty check + pack freshness vs shipped tags) | ✗ | ✗ | ✗ | ✗ |
| Vertical 9:16, 1080×1920, captions | ✓ (ASS karaoke, ≤4 words/line) | ✓ (7 caption styles) | ✓ (+5 Pro looks) | ✓ | ✓ (5 styles) |
| Pro edit (jump cuts, zoom punch, grade, memes, sound design) | ◐ (FFmpeg filters; cut-to-speaker NOT in v1) | ✗ | ✓ | ✗ | ◐ (zooms + SFX; no jump cuts / meme layer described) |
| Storyline / multi-beat arc | ◐ (2–5 beats setup→turn→payoff; no live end-to-end render yet) | ✗ | ✓ | ✗ | ◐ (story CHECK, not an arc) |
| Full posting pack (description + tags + first comment) | ✓ (Template A, 10 fresh tags, first comment +60 min, self-checked) | ✗ (titles only, as described) | ✗ (titles only) | ◐ (title + caption + hashtags `.txt`; no description/tags/first comment) | ◐ (caption, hashtags, 2 A/B hooks; no description/tags/first comment) |
| Music-rights screening | ◐ (MODERATE flags + listen-check; no automated screen) | ✗ (not stated) | ✗ (same) | ✗ (not stated) | ✗ (warns music lowers Shorts payout) |
| Originality / reused-content guard | ◐ (Purple gate + layout + uniqueness check; no narration module in v1) | ✗ | ✗ | ✗ | ✗ |
| Phone app / remote approve | ✗ | ✗ | ✓ | ✗ | ✗ |
| Auto-upload / scheduling | ✗ (manual upload; private-then-scheduled pattern is the Phase-2 design) | ✗ | ◐ (coming soon) | ✗ | ✗ |
| Fix Blur (AI-sharpened facecams) | ✗ (ffmpeg `unsharp` only) | ✗ | ✓ | ✗ | ✗ |
| Paid clipping campaigns (rules built in) | ✗ (monetisation is a separate skill, not engine v1) | ✗ | ✓ | ✗ (implied only) | ◐ (rate table + guidance, no built-in rules) |

**Where v1 wins, honestly:** permission allowlist enforcement,
uniqueness/duplicate check, Purple remarkability gate, full posting
pack (description + fresh tags + first comment, self-checked),
deterministic scoring with a veto, Linux support, pro-edit effects as
$0 FFmpeg filters — all at $0 with no clip cap.
**Where it is still behind Motion Mania Pro:** phone approval,
auto-upload (coming soon there too), AI-sharpened facecams, built-in
campaign rules, polished GUI editor.
**Where it is still behind the field:** live clipping proven end to
end (Motion Mania has it; ours is spec'd), LLM judge benchmarked
(not yet run).

**Honesty note (read first).** The v1 column above describes the v1
DESIGN plus the modules on disk in the reference build as listed on
2026-11-23 — it is NOT a claim that every component is finished.
Where a cell is ◐, the note says exactly what is missing. Every
Motion Mania claim traces to its pricing/features pages fetched live
2026-11-23 or its launch-video transcripts — no Motion Mania claim
comes from anywhere else.

**Other comparables checked 2026-11-23:** OpusClip (skills.sh) — a
paid clip-pipeline skill; its Virality Score is triage, not truth
(~40% of generated clips get discarded in the only credible
independent test), and billing is 1 credit = 1 minute of SOURCE video
regardless of clips out. Reap (skills.sh) — a paid REST API for AI
clipping/captions/reframing/publishing, not a local engine.
`clipping-agency-skill` (skills.sh) — an agency retainer workflow
(client ledgers, approvals, monthly reports), not a clipping engine.
No other free local stream-clipping engine skill was found in the
skill directories (Skills Directory, askill.sh, Skillstore, skills.sh,
claudepluginhub.com, skillsllm.com), on GitHub, or on YouTube beyond
gta6-clipper, beyondgtaclips, and Motion Mania.

**Licence rules:** beyondgtaclips = custom all-rights-reserved
(reference ONLY — never copy its code/text, never redistribute).
gta6-clipper / ClipIt / auto-caption / reelforge = MIT (forkable).
R3LAMP4GO / streamclipper / Clips Kitty = AGPL (copyleft — respect
it). Re-check each LICENSE file before reusing code.

## 10. What v1 is NOT (do not promise these)

- **No phone app / remote approval** (Motion Mania Pro). v1 = files on
  disk + manual upload.
- **No auto-upload / scheduling.** The only $0 route needs the user's
  own API credentials + platform review.
- **No AI face-sharpening** (Motion Mania Pro "Fix Blur"). v1 ships
  ffmpeg `unsharp` only — do not promise AI upscaling.
- **No true web app.** Motion Mania is a DESKTOP app with a landing
  page, not a web app. A true web app is never $0 at scale — the cost
  driver is source-video length (faster-whisper base on 2 vCPU runs
  ≈5.3× real-time, per the web-version research — an estimate, not a
  measurement on the reference build). Recommended path: Tauri desktop
  app first (Python engine as a PyInstaller sidecar, genuinely $0 at
  any scale — the same architecture Motion Mania uses; ship unsigned
  v1 $0, Apple signing $99/yr only when downloads justify it) + a
  static landing page ($0) + a capped HF Spaces ZeroGPU demo (~3–5
  clips/day, 90 s max source). Defer the true web app (FastAPI +
  queue + R2 + Modal workers) until revenue exists, priced per
  source-minute from day one.
- **No narration / originality module in v1.** The Oct 1 2026
  originality update deprioritises re-uploaded clips even with
  permission + credit. The Purple gate + house layout + curation is
  v1's answer; own-voice commentary is a separate, owner-gated
  decision.
- **No live clipping in v1.** VOD-first. Live is v2 (streamlink
  rolling buffer pattern from gta6-clipper's live buffer — design
  only, not run end to end).
- **No LLM judge in v1.** Deterministic score + human Purple gate
  only (§5.2).

## 11. Proof it works — reference build (2026-11-23)

The reference build this skill documents was verified end to end on
2026-11-23. These are dated evidence for the design, not a promise
that your install passes — re-run the tests on your machine.

- **143 tests, all green:** 61 in `src/tests` (core, scoring,
  presets, render incl. words-to-SRT gaps; 1 skipped), 63 in `tests/`
  (pack, render, pro-edit, storyline), 19 in the standalone
  chat/face/emotion runner. Re-run: §3.
- **2 finished test Shorts, both verified by ffprobe + frame checks:**
  45.03 s and 50.02 s, both 1080×1920, 60 fps, h264+aac, from one
  permission-cleared streamer's VOD. Loudness spikes fired on real
  material (9.05 LU and 9.5 LU deltas, the +9 dB rule). Emotion
  samples read (rage 0.437 on the second clip). Fusion score 22.8 on
  the second clip. Both are pipeline demonstrations, NOT new-ship
  recommendations — both beats had already shipped, so the novelty
  gate correctly forces N=0 and `ship: False`.
- **Gate proven by refusal:** re-running the pack builder on the
  second clip's scored candidate on 2026-11-23 raised `PackError:
  purple total 6/10 is below the 7/10 ship threshold` — the gate
  blocks a below-threshold pack instead of returning one.
- **Defects found on real material and fixed:** (1) a single
  ffmpeg audio+video download silently truncated audio to ~0.02 s —
  audio and video are now downloaded separately, then muxed; (2) a
  Whisper hallucination loop was caught and discarded — VTT is now
  the subtitle source of truth; (3) a burned subtitle collided with
  the game's own legible caption — verbatim-duplicate burned events
  are now dropped and the render re-run; (4) `loudnorm input_i`
  metering double-counts the tail (ffmpeg ≤8.1.1) — metering is now
  `ebur128` only; (5) `/tmp` is a 512 MB tmpfs that filled and killed
  a wav extraction — scratch is now the workspace disk only.

## 12. Troubleshooting

| Symptom | Likely cause → fix |
|---|---|
| `PackError: purple P=0` | Promised beat absent/exaggerated — pick another moment, do not reword the title to fit |
| `PackError: could not build a title / L1 / L2` | Hook or title_idea too vague/short — rewrite the hook from the transcript, never pad with invented detail |
| `PackError: could only build N/7 fresh content tags` | Moment keywords collide with shipped tags — add a more specific hook/transcript detail |
| `PackError: purple total 6/10 is below the 7/10 ship threshold` | Gate working as designed — rework the angle or pick another moment; do not lower the threshold |
| yt-dlp fails with SSL errors after a VM restart | SSL CA rotated — restore pristine certifi + append current egress CA (re-apply after every restart) |
| faster-whisper slow / OOM | Transcribing too much — windows only (30–90 s), `tiny`/`base` int8, beam 1–3, `OMP_NUM_THREADS=2`; never `medium`/`large` on a weak machine |
| Chat download empty | Chat disabled/deleted/sub-only, or `chat-downloader` broke on a YouTube change — fallback `yt-dlp --write-subs --sub-langs live_chat`; Twitch fallback `yt-dlp --sub-langs rechat` |
| Kick has no chat signal | Known gap (Phase 1) — Kick = loudness + transcript + face only until a Kick chat source is tested |
| `loudnorm` reading looks wrong | Never meter with `loudnorm input_i` (tail double-count bug, ffmpeg ≤8.1.1) — meter with `ebur128` |
| Tests fail in `tests/` but not `tests/test_pack.py` | Another module's tests — do not "fix" them by editing their module; report the failure with the test name |

## 13. Open items / Phase 2 (do not paper over these)

- Ollama Qwen judge unbenchmarked — shortlist size and chunk length
  need a measured run before the judge is trusted (§5.2).
- Live clipping: streamlink rolling buffer design only; needs a live
  end-to-end run.
- Kick chat: no mature downloader — Kick is discovery-only in v1.
- Twitch chat download not yet verified end to end on a real cleared
  streamer's Twitch VOD (CLI works; needs a VOD id).
- Hald LUT path built but palette-chart validation (±1 code value)
  has not run on a real reel.
- Storyline has no live end-to-end render yet.
- Discovery is slow live (~149 s for 5 results, full per-video
  extraction — measured on the reference build).
- Cut-to-speaker and Fix Blur are not in v1.
- Pack L1/L2 are template-built: they are true and gate-passing, but
  a human watch-through still adds the specific details a template
  can't know; the 7th tag stem can read slightly awkward — human tag
  pass recommended before shipping.
- WhisperX diarization needs a HF token for its gated model — do NOT
  use diarization in the $0 engine; the mouth-movement proxy is the
  Phase-2 alternative.

## 14. Sources

- Reference build (Nov 23 2026): engine root `[ENGINE_ROOT]` —
  `README.md`, `FEATURE-MATRIX.md`, `research/` (web/skills/GitHub
  search, components PyPI/npm/Hugging Face, YouTube transcripts,
  skill comparison, web-version architecture). The author's reference
  build used `[ENGINE_ROOT]` as its root; the skill
  text uses `[ENGINE_ROOT]` / `[ENGINE_PKG]` so it works anywhere.
- Motion Mania pricing + features, live fetch 2026-11-23
  (motionmania.app/pricing, motionmania.app/features).
- Motion Mania transcripts (PreMania videos, pickiness 18→6, Pro
  Edit / Storyline / phone app descriptions).
- gta6-clipper: skills.sh listing + YouTube demo (39 possible → 3
  kept, 4 h 09 min → 13 min 48 s run; Mac-only; Claude $20/mo or
  free Ollama Qwen). **Conflict noted:** the README describes a live
  clipper (~5–8 min after the moment); the video transcript claims
  no live-stream watching. The comparison marks live as ◐ and cites
  both.
- beyondgtaclips: skillsllm.com listing + GitHub
  (beyondtahir/beyondgtaclips). Licence: custom all-rights-reserved
  — reference only, never copied.
- OpusClip, Reap, clipping-agency-skill: skills.sh listings, checked
  2026-11-23.
- YouTube Help: Shorts originality update (Oct 1 2026); Shorts
  discovery; tags; descriptions; hashtags.
- Returbe title study (63,480 videos, Nov 2026) for the 40–60 char
  gaming-Shorts title band.
