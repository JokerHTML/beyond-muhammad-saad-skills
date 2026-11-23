---
name: post-publish-qa
description: Verify a social post before it goes out and after it lands — account check, duplicate check, live read-back, failure and concurrent-run guards across every platform.
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
---

# Post-Publish QA

## Purpose

Verify a social post **before** it goes out and **after** it lands. A post counts as published only when it is **verified live on the intended account** — not when a schedule command returns success, and not when a publish call returns without an error.

## When to Use

- Before publishing or scheduling any post, on any platform.
- After every publish, scheduled or immediate, before moving to the next slot.
- Before any second delivery attempt, retry, or completion pass.

## The Two Log Files

The collision guard and the duplicate guard both depend on these two files. Define them **before your first run** — a guard that reads a file that doesn't exist is not a guard.

### 1. Published log — `[your published log path]`

One line per write, appended **immediately** after it lands. Format (one line per write, fields separated by ` | `):

```
YYYY-MM-DD HH:MM TZ | platform | account/handle | slot-id | post URL or id | caption-file version | status (POSTED / SCHEDULED / FAILED / UNKNOWN)
```

Example:

```
2026-11-23 20:00 PKT | Threads | [your Threads handle] | TEST-001 | [live post URL] | caption v2 | POSTED
```

### 2. Day-counts file — `[your day-counts file path]`

One section per platform, updated on every write. Format:

```
[Platform] — YYYY-MM-DD
cap: [user-configured daily cap, e.g. 20]
writes today: N (list each slot-id)
reserved: N (scheduled fires + reserved first replies, list each)
headroom: cap - writes - reserved
last write: YYYY-MM-DD HH:MM TZ (slot-id)
```

Both files live wherever you keep your publishing records (e.g. `[your workspace]/publishing/`). The exact path is yours; the format above is not optional.

## Pre-Publish Record Template

Write one record per slot **before** publishing. Fields:

- slot-id | platform | account checked (name/handle/Page ID) | caption-file name + version | media file name | duplicate-check result (MATCH / NO MATCH + what was compared) | session check (signed in as correct account: YES/NO) | first read time | second read time (for threaded replies) | decision (GO / STOP + reason)

## Check Before You Publish

- Open the **correct account first** and confirm the account name and handle/Page ID before you touch any publish or schedule control. If you manage more than one Page or profile, confirm you are inside the right one — never the duplicate or personal one.
- Confirm each platform uses the intended account: Facebook → `[your Page name + Page ID]`; Instagram / Threads / X → `[your handles]`; Pinterest → `[your Pinterest account]`, and read its recent pins before you publish or schedule a pin.
- Read the **recent posts on that exact account** before you publish or schedule anything.
- Compare the slot caption and media against those recent posts and **stop** when you find the same caption or media already live.
- Read the caption file again at publish time and confirm it is the **latest fixed version**, not an earlier draft. One caption file per slot is the single source of truth — fix it there, never by editing live text.
- Confirm the media file named in the batch matches the caption and **opens without corruption**.
- Confirm the account session is signed in as the correct account before you schedule. If it is signed out, **stop and report a blocker** — never publish blind.
- Check the brief and the platform fit: caption adapted for this platform, asset size right, link/CTA valid for this platform, any required disclosure present, publish time and timezone correct.
- Write one pre-publish record for the slot (template above).

## Verify After You Publish

Run this within minutes of the post landing (a two-minute live check catches most rendering defects):

- Open the **live URL** returned by the publish call. If no URL was returned, fetch the post from the account's recent posts.
- Compare the live text with the caption file **byte for byte** and fail the post on any hashtag or wording mismatch.
- Check that images load at full size and that video plays for the **full source duration**.
- Check that links appear only where the platform allows them — never as a raw link in a Threads body.
- Check formatting for literal asterisks, broken unicode, and collapsed line breaks; fail the post on any corruption.
- Confirm **public visibility** through a read that does not rely on the owner session, where possible.
- Check recent posts again for an accidental duplicate and treat a duplicate as a defect.
- Verify any product comment or self-reply on product posts, with the exact product URL in the correct place.
- Write one verification record per post: date | platform | slot-id | status (PASS / FAIL) | live URL | problem (or "none").

## Handle Failures

- **Stop the batch on any defect.** Do not continue to the next slot until the defect is resolved or the account owner explicitly waives it.
- **Check the live surface first when a publish result is uncertain** — never retry a publish before that check. A failed or stuck write can still be delivered later; a blind retry creates a duplicate.
- **Treat a failed/stuck write as possibly delivered later** and re-check the live surface before you publish a replacement.
- Ask for approval before you delete any live post. **Never delete automatically.**
- Stop after **three genuine verification attempts** when a live post cannot be reached, and report the blocker.

## Re-Read After a Lag Before Any Second Delivery

A zero result is **unverified, not proof of absence** — an earlier run may already have delivered the same slot without a report.

- Read the **nested replies in the thread itself**, not only the top-level recent-posts list, before you publish a threaded reply.
- Wait for the threaded surface to settle and **re-read the live thread a second time after a short delay** when the first read shows no matching reply.
- Check the published log and any delivery record for the slot before you make a second delivery attempt in a completion pass.
- **Stop and report the slot as unverified** when the second read still cannot confirm absence, instead of publishing a second copy.
- Record both reads with their times and results in the pre-publish record for the slot.

## Guard Against Concurrent Runs

- Check whether another publish or engagement run is working at the same time before you start your run.
- Read the published log and the day-counts file and note the time of the most recent write before your first write.
- **Stop and report the collision** when the log shows a write by another run in the last **15 minutes** and you cannot tell which run owns the slot.
- Re-read the day-counts file **immediately before each reply or post**, not once at the start of the run.
- Re-read the live thread immediately before each threaded reply and stop when a matching reply is already there.
- Log each write in the published log **immediately** after it lands so a run that starts later can see it.
- Never assume a cap has headroom from a count you read before another run started.
- For multi-channel delivery, track each destination separately so recovering one failure cannot duplicate a post that already succeeded on another destination.

## Platform Routes

- **Facebook:** `[Facebook connector / tool you use]` for Page posts, recent posts, and comments.
- **Instagram:** `[Instagram connector / tool you use]` for feed posts, reels, carousels, and recent posts.
- **Threads:** `[Threads connector / tool you use]` for posts, replies, and recent posts.
- **X:** `[X connector / tool you use]` for posts and recent posts.
- **Pinterest — named route:** the **official Pinterest API v5** (`POST /v5/pins`, scopes `pins:read`, `pins:write`, `boards:read`, `boards:write`) for creating pins and reading boards/recent pins. **Scheduling note (unverified — do not rely on it):** some 2026 guides report a `publish_at` field for native scheduled pins (≥10 minutes out, ≤30 days out); other 2026 guides report the Create Pin endpoint has no scheduling field and every scheduler builds its own queue. Until you verify `publish_at` against the official Pinterest developer docs for your own app access tier, treat API scheduling as **unconfirmed**.
- **Pinterest — fallback (explicit):** if the API route is unavailable or scheduling is unconfirmed, publish/schedule pins **directly in Pinterest's own Create tab / native scheduler** (file upload only — never Save-from-URL, which locks the image URL as an unremovable destination link), or through an approved partner scheduler (e.g. Tailwind, Later). Verify the live pin after publishing either way — never trust the publish result alone.
- **Any other platform:** search for a maintained connector or official API first; if none fits, look on the web for a maintained API or MCP server and set it up through your connector-setup workflow. Never invent a connector.

## Alternatives for Better Results

- Schedule inside each platform's native scheduler and verify the slot in that platform's scheduled list, rather than trusting a schedule command.
- Keep one caption file per slot as the single source of truth and fix it there rather than editing live text.
- Track each destination separately so recovering one failure cannot duplicate a post that already succeeded on another destination.
- For Pinterest, check recent pins before you publish and verify the live pin after you publish rather than trusting the publish result.
