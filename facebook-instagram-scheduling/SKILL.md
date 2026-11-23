---
name: facebook-instagram-scheduling
description: Schedule Facebook and Instagram posts free — native composer and CLI routes, exact times, duplicate guards, and live verification, so no slot goes out twice or at the wrong hour.
version: 1.1.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
updated: 2026-11-23
---

# Facebook + Instagram Scheduling

**Scope:** scheduling and publishing posts to one Facebook Page and one Instagram account you manage, from native routes — no third-party scheduler subscription required. **Tools (named):** `facebook-cli` (`/opt/hatch/bin/facebook-cli`) for Facebook Pages, `instagram-cli` (`/opt/hatch/bin/instagram-cli`) for Instagram. Both CLIs are the documented connectors for their platforms; read their connector docs before a first write. **Companion skill:** your post-publish QA checklist (account, caption, media, time) — run it before anything is scheduled; see section 1.

---

## 1. Pre-flight checklist (run before every slot)

Run this before any scheduling attempt, on either network. It replaces any brand-specific QA check: the checks are the same for every account.

- [ ] **Account:** confirm the active Page / Instagram account from details already shown on the surface (Page name in the composer header, `facebook-cli pages list`, `instagram-cli accounts`). Do not click the account switcher to verify the Page mid-flow — switching accounts can drop the session. If the account shown is not the intended one, stop and resolve it before touching the post.
- [ ] **Caption file:** one caption file per slot is the single source of truth (for example `slots/<slot-id>/caption.txt`). The scheduled text is copied verbatim from it. Fix copy in the file, never by editing live text after scheduling.
- [ ] **Media:** every file exists under `~/workspace/`, is the right format and size (see section 5), and is attached in final order. Never pass a `/tmp` path to `instagram-cli`.
- [ ] **Time:** the slot time is written down in all four forms (section 2) and is inside the route's window. Never schedule from a bare "8 pm" — always with date, timezone, and the exact flag value.
- [ ] **Approval:** the exact text, media order, destination account, and scheduled time were approved as one unit. If any of the four changes after approval, re-approve before scheduling.

---

## 2. Time specification — the rule for every scheduled time

Every scheduled time is recorded in all four forms before it is used. No exceptions: most scheduling failures in this workflow are timezone or format errors, not platform errors.

| Form | Example (verified by a real conversion run) |
|---|---|
| Local date + time + IANA timezone | 2026-11-24, 20:00, Asia/Karachi |
| UTC equivalent | 2026-11-24T15:00:00Z |
| Facebook CLI value | Unix seconds: `1795532400` |
| Instagram CLI value | RFC 3339 with explicit offset: `2026-11-24T20:00:00+05:00` |

- **Facebook CLI** (`facebook-cli pages posts create`, `pages drafts publish`): `--scheduled-publish-time <Unix seconds>`. Window: **10 minutes to 29 days ahead**. Unix seconds are timezone-agnostic once converted — convert from the local time in the slot's IANA timezone, and record the UTC equivalent alongside so the conversion is checkable. Reschedule with `pages posts reschedule` (same Unix-seconds value, new time); cancel with `pages posts cancel-schedule` (post must be more than 5 minutes from publishing).
- **Instagram CLI** (`instagram-cli post-feed`, `instagram-cli post-story`): `--publish-at <RFC 3339 with explicit offset>`, for example `2026-10-17T15:30:00-07:00`. Omit the flag to publish immediately. No minimum lead time is documented for this CLI — schedule at least 10 minutes out as house practice, matching the Facebook floor, so the timed run and any approval step have margin. A time without an offset is rejected: always include it.
- **Facebook composer / Meta Business Suite UI:** times are picked in the timezone the browser shows for the account. Suite allows scheduling **20 minutes to 29 days ahead** (UI floor is 20 minutes; the CLI floor is 10 — the difference is real, use the floor of the route you are on). Confirm the timezone shown in the picker matches the slot's IANA timezone before saving.
- **Conversion check (run it, do not trust mental arithmetic):** `TZ='<IANA timezone>' date -d '<local date time>' '+%Y-%m-%dT%H:%M:%S%z -> unix %s'` and `date -d '<local date time><offset>' -u '+%Y-%m-%dT%H:%M:%SZ'`. Both outputs must agree with the recorded UTC equivalent before the time is used. Re-checked 2026-11-23: 2026-11-25 20:00 Asia/Karachi = Unix `1795618800` = `2026-11-25T15:00:00Z` — the method reproduces exactly.

---

## 3. Facebook — schedule from the Page composer first

Route order: composer → CLI → Suite-if-it-works → owner device. Do not start at Suite, and do not return to a route that already failed for the same slot without a new mechanism.

### 3.1 Composer route (first choice)

1. Open facebook.com, go to the Page, open the composer ("What's on your mind?").
2. Paste the caption verbatim from the slot's caption file. Do not retype it.
3. Attach the image through the composer drop zone. **Caution (observed in one environment, verify in the live composer before relying on it):** do not use the hidden Choose File control for a PNG — it can misroute the image into the Reel creator with nothing published.
4. Open Scheduling options, set the date and time (section 2), save, and click Schedule.
5. Verify the slot in the scheduled posts view: scheduled time, public visibility, attached image, verbatim caption. Report a scheduled time only after this verification.

### 3.2 CLI route (fallback when the composer route fails)

Use `facebook-cli` — it schedules Page posts without a browser session:

```sh
# Schedule directly (no draft kept)
facebook-cli pages posts create --page-id '<page_id>' --text '<exact text>' \
  --privacy PUBLIC --file ~/workspace/<image>.jpg \
  --scheduled-publish-time <unix-seconds>

# Or save a draft first, then schedule it (lets another admin review first)
facebook-cli pages drafts create --page-id '<page_id>' --text '<exact text>' \
  --file ~/workspace/<image>.jpg
facebook-cli pages drafts publish --page-id '<page_id>' --draft-id '<draft_id>' \
  --privacy PUBLIC --scheduled-publish-time <unix-seconds>
```

- A Page post whose only media is one MP4 publishes as a Reel. Use `posts create` with one MP4 `--file` to publish or schedule it directly.
- Confirm the outcome from the returned state only: `state: scheduled` means publication is pending; `state: published` confirms publication. A post ID with an unknown outcome proves neither — ask the user to check the Page, or check the scheduled view, before any retry.
- Reschedule or cancel with `pages posts reschedule` / `pages posts cancel-schedule` (section 2). Cancelling turns the post back into a draft, though a publisher already running may still publish it.

### 3.3 Meta Business Suite — use only if its upload works in your environment

- Suite is Meta's own supported scheduler (it schedules Page posts 20 minutes to 29 days ahead and can post to Facebook and Instagram together). It is a legitimate route — **unless its upload or schedule control fails in your environment**. If you have seen Suite's upload button fail repeatedly with no new mechanism, do not keep retrying it: use the composer (3.1) or the CLI (3.2) instead, and revisit Suite only when something has changed (a new browser profile, a new mechanism, or a fix from Meta).
- Scheduled Page posts live in Suite under Content → Posts and reels → Scheduled tab. That is the visual verification surface for Suite-scheduled slots.
- Never retry Suite scheduling without a new mechanism, because repeated identical retries have already proved the same failure.
- Paid Meta One plans extend native scheduling on mobile (reported in 2026 guides, per Meta's Help Center: up to 365 days on Advanced/Expert/Max) — the free 29-day ceiling above is the default. If a slot needs further than 29 days, check the plan before promising the date.

### 3.4 Owner-device route

- When the owner is available to post from their own device, that is a valid route — use the Facebook app's composer scheduling (What's on your mind? → Next → Schedule). Keep the timed CLI run as the backup so the slot still has a fire time if the device post does not happen.

---

## 4. Instagram — publish with a duplicate-guarded timed CLI run

Instagram has no composer-scheduling equivalent of Facebook's in this workflow. The route is a scheduled job that fires `instagram-cli` at the slot time, guarded so it can never publish twice.

### 4.1 The timed run

1. Write the slot record first: slot ID, account, caption file path, media files in order, fire time in all four forms (section 2), and status `scheduled`. One file per slot, for example `slots/<slot-id>/slot.json`. The slot record is the duplicate guard — the CLI cannot list scheduled Instagram content, so the guard lives in your own ledger, not in an API query.
2. Create the timed job (cron or `at`) to run at the fire time. The job does, in order:
   a. Read the slot record. If status is not `scheduled`, exit without posting.
   b. Check the profile posts list for the slot's content. If the post is already live, mark the slot `live`, exit without posting.
   c. Run `post-feed` (or `post-story`) with `--publish-at` omitted — the job itself is the timer, so the CLI publishes immediately on a successful run. (Alternative: pass `--publish-at` with the fire time when creating the job instead of running at the fire time; pick one mechanism per slot, never both.)
   d. On success, mark the slot `live` with the returned post URL. On error, mark it `uncertain` — do not retry yet (section 6).
3. Make the timed run skip itself when the slot is already scheduled or already live. The check is the slot record plus the live profile surface — never a bare re-run.

### 4.2 Commands (named CLI: `instagram-cli`)

```sh
# Resolve the account first (once per session)
/opt/hatch/bin/instagram-cli accounts

# Image post (portrait 4:5 1080x1350 or square 1:1 1080x1080 preferred)
/opt/hatch/bin/instagram-cli post-feed --account-id <user_own_fbid> \
  --file ~/workspace/<image>.jpg --caption '<caption>'

# Reel shared to the feed (vertical 9:16 1080x1920; video needs a cover)
/opt/hatch/bin/instagram-cli post-feed --account-id <user_own_fbid> \
  --file ~/workspace/<reel>.mp4 --cover ~/workspace/<cover>.jpg \
  --video-thumbnail-playback-offset-ms 1200 --caption '<caption>'

# Carousel (two or more files, same aspect ratio and size, in display order)
/opt/hatch/bin/instagram-cli post-feed --account-id <user_own_fbid> \
  --file ~/workspace/<first>.jpg --file ~/workspace/<second>.mp4 \
  --cover ~/workspace/<second-cover>.jpg --caption '<caption>'

# Schedule instead of publishing now (same commands, plus the flag)
/opt/hatch/bin/instagram-cli post-feed --account-id <user_own_fbid> \
  --file ~/workspace/<image>.jpg --caption '<caption>' \
  --publish-at '2026-11-24T20:00:00+05:00'
```

- `--account-id` is required on every command except `accounts`, `connect-url`, `disconnect-url`, and `--help`. Take it from `accounts` output in the same session; never guess it and never pass another person's ID.
- `--retries` must stay `0` for writes (`post-feed`, `post-story`, and other writes reject any other value): a retry can publish a duplicate. Never start the same publish again while its command or a scheduled job for it is still running.
- If scheduling returns `Meta One Required`, the account needs Advanced content scheduling in its Meta One plan. Report what the error says and re-plan; do not automatically retry that scheduling request.
- `instagram-cli` cannot list, edit, or cancel scheduled content, and `posts` does not show it until it publishes. If a scheduled post must change, point the user to scheduled content in the Instagram app — do not schedule a replacement while the original is still scheduled.
- Stories: `post-story` takes the same `--publish-at`. For edited stories, render with `--draft` + `--editor-json` first, get the rendered draft approved, then rerun without `--draft` to publish. An edited story is never published from delegated work without approval of the rendered draft.

### 4.3 Owner-device backup

- Keep the owner-device route (Instagram app) as the backup when the owner is available, and the timed CLI run as the other backup — one of the two must hold the fire time for every slot. Never leave a slot with no fire mechanism.

---

## 5. Limits — check before you build the slot

| Item | Limit | Source |
|---|---|---|
| Facebook CLI Page post text | 1,024 characters max, no leading/trailing spaces (CLI limit — the composer allows more) | `facebook-cli pages posts create --help` |
| Facebook CLI media | PNG/JPEG up to 10 MiB, or MP4; up to 80 files, in post order | `facebook-cli` pages-publishing docs |
| Facebook schedule window (CLI) | 10 minutes to 29 days ahead | `facebook-cli` pages-publishing docs |
| Facebook schedule window (Suite UI) | 20 minutes to 29 days ahead | Meta / Suite guides, 2026 |
| Instagram caption | 2,200 characters max; whitespace-only counts as absent | `instagram-cli` connector docs |
| Instagram media | Each file at most 100 MB; files must live under `~/workspace/` | `instagram-cli` connector docs |
| Instagram image post | Portrait 4:5 at 1080x1350 or square 1:1 at 1080x1080 preferred | `instagram-cli` connector docs |
| Instagram reel | Vertical 9:16 at 1080x1920; video needs a JPEG/PNG/WebP `--cover` | `instagram-cli` connector docs |
| Instagram carousel | 2+ files, same aspect ratio and size; covers repeat once per video, in video order | `instagram-cli` connector docs |
| Instagram daily publishing limit | Instagram enforces a per-account daily publishing limit — a failed or uncertain attempt may already have published and counts toward it | `instagram-cli` connector docs |

---

## 6. Verify before you retry or report

- **Re-read the live or scheduled surface before any retry.** A failed or stuck write can still execute later — a connector write that "failed" with a stuck lock, or a CLI publish that returned HTTP 500, can go live minutes or hours after the error. Check the profile posts list after any CLI result that reports an error, because an error result does not prove the publish failed. Never retry a CLI publish before you check the live profile surface for the post.
- **Report a scheduled time or a live link only after you verified it** in the scheduled list or on the live surface. A post ID with an unknown outcome is not a confirmation.
- **On HTTP 429 (rate limit):** stop every CLI call for the task, including calls from scripts. Report what completed and what remains. Do not sleep-and-retry inside the same task.
- **On HTTP 403 saying an operation is unavailable:** the operation is disabled for the account. Reconnecting does not fix it — report it as unavailable.
- **Leave a slot unscheduled and report the blocker plainly** when every route in this skill has failed, instead of returning to a route that already failed for that slot. A missed slot with a clear blocker is better than a duplicate post.
- **After an unknown outcome** (timeout, disconnect, malformed receipt, refusal): ask the user to check the Page, post, or draft in the app. Do not attempt another write unless the user asks.

---

## 7. When the native routes cannot do it

- If the composer, the CLI, Suite-when-it-works, and the owner device have all failed for a slot, the next options are third-party schedulers — Buffer, Social Post Flow (`spf` CLI), SocialClaw, or Publora — which schedule Facebook and Instagram through their own APIs. Trade-off, stated plainly: they need a separate account, their own auth to your Pages, and usually a paid plan for scheduling; they also own the retry and duplicate-guard logic, so verify what happens on a failed publish before trusting one with a live slot. Prefer the native routes in sections 3–4; use a third-party tool only when the native routes are blocked, not as the default.
- If no route fits, look for a maintained API or MCP server and set it up with the custom-connector setup skill — do not hand-roll a scraper or a browser bot for posting.

---

## Available connectors

- [Facebook](/opt/hatch/connectors/facebook_cli/CONNECTOR.md) — Page posts, drafts, schedules, recent posts and comments. Commands run through `/opt/hatch/bin/facebook-cli`.
- [Instagram](/opt/hatch/connectors/instagram/CONNECTOR.md) — feed posts, reels, carousels, stories, recent posts. Commands run through `/opt/hatch/bin/instagram-cli`.

## Websites

- [Facebook](https://www.facebook.com/) for Page composer scheduling. Carry the exact approved text and media and publication time into the browser task and verify the slot in the scheduled posts view.
- [Meta Business Suite](https://business.facebook.com/) — Content → Posts and reels → Scheduled tab is the visual verification surface for Suite-scheduled slots. Use only if its upload works in your environment (section 3.3).

## Alternatives for better results

- Use the owner device route when the owner is available to post from the device, and keep the timed CLI run as the backup so the slot still has a fire time.
- Keep one caption file per slot as the single source of truth, and fix copy there rather than editing live text after scheduling.
- Validate before you publish: the pre-flight checklist (section 1) plus approval of the exact text, media, account, and time as one unit, then a status check after the fire time. Third-party scheduling skills add an explicit validate step before any apply — this skill does the same with the checklist, without needing their service.
