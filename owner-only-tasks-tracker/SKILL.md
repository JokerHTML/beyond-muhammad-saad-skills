---
name: owner-only-tasks-tracker
description: Track every task only the account owner can do — logins, approvals, phone steps, owner-only decisions — in one queue that re-surfaces on a 3/7/14-day cadence, so nothing waits silently.
version: 1.1.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
updated: 2026-11-23
---

# Owner-Only Tasks Tracker

Use this when a step you need can only be done by the owner: a login, a session approval, a phone-side action, a platform identity check, or a decision only they can make. The gate gets logged once, re-surfaced on a schedule, and closed only on verification, so it never ages silently.

This is not the human-comment-replies skill. That skill is about replying to other people like a human. This skill is about tracking work that is blocked on the owner.

## The queue

Keep one queue in your log file — the durable notes file every session and scheduled run can read (for example your main memory or operations log). One line per gate, in this fixed format. Never keep gates in a separate file that sessions do not read, and never in chat alone — chat scrolls away, the log does not.

```
[GATE-ID] | OPENED: [date] | ASKED: [dates, comma-separated] | GATE: [one line — what is blocked] | STEPS: [exact steps for the owner] | DUE: [date the decision/action is needed by, or — ] | BACKUP: [who can decide if the owner is unavailable, or — ] | IMPACT: [what is blocked / what it unblocks] | STAGED: [what is ready to go the moment the gate clears] | STATUS: OPEN
```

Field rules:
- **GATE-ID** — sequential, e.g. `G-001`. One ID per gate, never reused, never renumbered.
- **GATE** — one line. The blocked step, not the whole project.
- **STEPS** — exact steps for the owner, in the order they do them. No "please log in" without where, what account, and what to click.
- **DUE** — the date the decision or action is needed by. A gate without a due date is a gate that drifts; if there is genuinely no deadline, write `—` and say so in IMPACT.
- **BACKUP** — the person authorised to decide if the owner is unavailable. Usually `—` for a solo owner; write the name when one exists.
- **IMPACT** — what is blocked and what resolving it unblocks, in one line. This is what makes the re-surface worth reading.
- **STAGED** — what is already prepared around the gate, so resolving it needs no rework. "Nothing staged" is a valid entry — it just has to be honest.
- **ASKED** — append every date the gate was asked about. Never rewrite history or merge two different gates into one line.

### Worked example — one gate, full lifecycle (illustrative, not a real gate)

```
G-014 | OPENED: 2026-11-20 | ASKED: 2026-11-20, 2026-11-23, 2026-11-27 | GATE: Phone verification for the clips channel (uploads blocked at daily limit) | STEPS: 1) Open YouTube Studio on the phone 2) Settings → Channel → Feature eligibility 3) Verify by phone number, enter the code | DUE: 2026-11-24 (next upload slot) | BACKUP: — | IMPACT: Blocks all new uploads; unblocks the Dec 1–9 scheduled batch | STAGED: 3 videos edited, described and queued; publish needs 1 click each once verified | STATUS: CLOSED 2026-11-27 — verified live in Studio (phone-verified badge shown), batch published
```

## Open a gate

- Log the gate in the queue the moment you ask the owner, before you move on. Record the date, the gate in one line, the exact steps, and the status OPEN.
- Report the ask in chat first, with exact steps and a timebox. The log is the queue. It never replaces the ask.
- Before opening a gate, confirm the blocker is real with three genuine attempts, across sessions when the failure looks transient. A flaky session is not a gate. (This is the try-first rule: never declare a blocker you have not actually tried to clear.)
- Pair each gate with its workaround status. Say plainly what is staged, what is blocked, and what resolving the gate unblocks.

## Re-surface the gate

- Read the queue at the start of every session and every run that touches the blocked area. Check which gates are still open and how long they have waited.
- Re-surface a gate older than 3 days with one chat line carrying the exact ask again. Mention the days waited so the owner sees the age.
- After 7 days, collect every stale gate into one short list, newest first, and post it at most once per day. Stop attaching gate asks to unrelated conversations.
- When the blocked work can proceed partly, stage everything around the gate. Resolving it later should need no rework.
- A gate with a DUE date that passes unresolved gets escalated, not just re-surfaced: one line naming the missed date and the impact, and a new due date or a keep-or-drop decision (see Close, below).

## Close the gate

- Close a gate when the owner confirms the action, when the action verifies live, or when the need disappears. Record the resolution date and how you verified it.
- Never close on assumption or because the run moved on. An unverified gate stays OPEN.
- After 14 days open, bring the gate to chat for a keep-or-drop decision. A dropped gate leaves the queue with a one-line reason and its asked history intact — the line is never deleted, only marked DROPPED with the date and reason.
- A gate is never bypassed by working around it in silence. If the work proceeded without the owner action, say so on the gate line and close it only when the need genuinely disappeared.

## States

| Status | Meaning |
|---|---|
| OPEN | Asked, waiting on the owner |
| STALE | Open 7+ days, on the daily list |
| CLOSED | Resolved and verified, with date + how verified |
| DROPPED | Owner decided not to do it, with reason and asked history intact |

## Available connectors

- No connector fits this task. The queue is a plain log file that every session and scheduled run can read — by design, no tooling.

## Alternatives for better results

- Before opening a gate, confirm the blocker is real with three genuine attempts, across sessions when the failure looks transient. A flaky session is not a gate.
- Pair each gate with its workaround status. Say plainly what is staged, what is blocked, and what resolving the gate unblocks.
- For teams, give each gate a named decision owner and a backup decision-maker, a decision due date, and an escalation path — the fields are already in the format above. For a solo owner, BACKUP is `—` and the owner is the decision-maker by default.
- Do not confuse this queue with an approval workflow: this skill tracks owner-only steps in a log. If you need a system that pauses an automated run until a human signs off, use an approval-gate workflow (pause → approve/reject → resume) instead, and log the pause here as a gate.
