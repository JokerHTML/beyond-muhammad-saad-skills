---
name: ai-agents-automation
description: Build working AI agents and no-code automations on n8n, Make or Zapier from a $0 start — pick the right tool by its billing unit, ship a tested workflow with a full agent prompt, and keep it inside its cost and safety limits. For beginners and solo creators who want automations that actually run.
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
---

# AI Agents & Workflow Automation

## Purpose

Teach repeatable AI-agent and automation builds a $0 beginner can actually follow — with exact steps, exact prompts, verified free tiers, and honest limits. Every build in this skill was run end to end or is labelled as a build guide, never presented as a working run it never had.

## When to use

- Building your first agent or workflow (research agent, inbox triage, content repurposing, lead capture, scheduled digest).
- Choosing between n8n, Make, and Zapier for a specific job.
- Turning a manual repeating task into a scheduled or triggered workflow.
- Writing the AI step (the prompt) inside any workflow.

## When NOT to use

- The job needs real code (a typed API client, a webhook receiver in your own app, a database migration). This skill stops where code starts.
- The job handles secrets, payment data, or other people's private data and you have not read §9 (security) first.
- You need an n8n node-by-node API reference. Use the official n8n skills (`npx skills add n8n-io/skills`) or the n8n docs for that; this skill teaches judgement and complete builds, not every node.

## Rules (hard)

- **Free-first, honestly priced.** n8n Community Edition is free *software*, self-hosted — the server and the upkeep cost real money and time; say so. Zapier Free is $0/mo for 100 tasks/mo and two-step Zaps only. Never present a paid-only path as free, and never quote a price without its last-checked date (§2).
- **Every build carries the full prompt block** (§6) for the agent's AI step. A workflow with a one-line prompt is a draft, not a build.
- **Never tell readers to paste passwords, private client info, or confidential data into a tool without checking its data controls first.**
- **No fabricated run.** A workflow shown as "working" must have been run, or be labelled as a build guide ("follow these steps — not yet run end to end").
- **One CTA per post** when a build is published as content.
- **Re-check prices on the day you publish.** Free tiers and limits change without notice; §2 is dated 2026-11-23 and will go stale.

## 1. The three tools, in one paragraph each

- **n8n** — visual workflow builder with a free self-hosted Community Edition and a paid cloud. Best when a workflow has many steps, loops, or an AI agent, because it bills per whole workflow run, not per step. Costs you server upkeep when self-hosted, and technical comfort.
- **Make** (formerly Integromat) — visual scenario builder, the cheapest managed start. Best when you want a visual builder with branching and the lowest first paid month. Bills per module action, so long scenarios cost more than they look.
- **Zapier** — the largest app catalogue (9,000+ apps) and the easiest to learn. Best for short two-app automations and for apps the other two do not cover. Bills per successful action step, so multi-step workflows get expensive fast; the free plan only allows two-step Zaps.

## 2. Verified pricing — last checked 2026-11-23

Re-check every figure on the vendor's own pricing page before you quote it or buy. Prices below are list prices, excluding tax.

| Tool | Free tier | First paid tier | What you are billed for |
|---|---|---|---|
| **n8n Cloud** | Community Edition: $0, self-hosted, unlimited executions (you pay for the server) | Starter €20/mo billed annually (€24/mo billed monthly), 2,500 executions/mo, 5 concurrent runs | One **execution** = one complete run of a workflow, however many steps it has |
| **Zapier** | $0, 100 tasks/mo, two-step Zaps only, 1 user, 15-minute polling | Professional from $19.99/mo billed annually ($29.99/mo billed monthly), 750 tasks/mo, multi-step Zaps, webhooks | One **task** = one successful action step; AI steps and some connectors can consume more than one task |
| **Make** | $0, 1,000 credits/mo, 2 active scenarios, 15-minute minimum interval, 5-minute max run | Core $9/mo billed annually ($10.59/mo billed monthly), 10,000 credits/mo, unlimited scenarios, 1-minute interval | One **credit** = one module action (Make renamed "operations" to "credits" in Aug 2026; same unit) |
| **ChatGPT** (drafting model) | $0, unlimited everyday text chats, subject to abuse guardrails; uploads, images, voice and deep research limited | Plus $20/mo (monthly billing only) | Chat use; API use is billed separately and is not included |
| **Claude** (drafting model) | $0, limited usage in rolling 5-hour and weekly windows; no fixed message count published | Pro $20/mo, or $17/mo billed annually ($200 up front) | Chat use in the same 5-hour/weekly windows; Claude Code included on Pro |

Sources: n8n.io/pricing, zapier.com/pricing, make.com/pricing (read via vendor pages and independent pricing reads dated Sep–Nov 2026); OpenAI and Anthropic pricing pages (Oct–Nov 2026). Currency note: n8n publishes prices in euros; Zapier and Make in US dollars.

### 2.1 The billing-unit math (do this before you pick)

The three tools bill different units, and at volume the gap is ~10x. Work it for YOUR workflow:

```
n8n:    monthly cost driver = runs per month (steps are free)
Make:   monthly cost driver = runs per month × modules per run
Zapier: monthly cost driver = runs per month × action steps per run
```

Worked example — a 4-module scenario that runs 30 times a day (900 runs/mo):

| Tool | Arithmetic | Result | Fits in |
|---|---|---|---|
| n8n | 900 runs = 900 executions | 900 executions | Starter (2,500) — or $0 self-hosted |
| Make | 900 runs × 4 modules = 3,600 credits | 3,600 credits | Free is 1,000 → needs Core ($9/mo) |
| Zapier | 900 runs × 3 actions = 2,700 tasks | 2,700 tasks | Free is 100 → needs Professional above the $19.99 / 750-task band; check the task slider for the exact band price |

Rules of thumb: under ~2,500 runs/mo with no technical staff → n8n Cloud Starter or Make Core. Many steps per run → n8n wins. Two apps, two steps → Zapier Free wins. No budget at all → Make Free (1,000 credits) or self-hosted n8n.

## 3. Pick the platform — decision table

| Constraint | Pick | Why |
|---|---|---|
| $0 budget, willing to run a server or local machine | n8n Community (self-hosted) | Unlimited executions; the only $0 path with no run cap |
| $0 budget, no server, simple workflows | Make Free | 1,000 credits/mo, 2 scenarios — enough for one real workflow |
| $0 budget, two-step automation, obscure app | Zapier Free | Widest app catalogue; 100 tasks/mo proves one idea |
| Many steps, loops, AI agent, branching | n8n | Per-execution billing; strongest AI-agent nodes |
| Cheapest first paid month | Make Core ($9/mo annual) | 10,000 credits; unlimited scenarios |
| Easiest to learn, team handover | Zapier Professional | Simplest builder; most tutorials exist |
| Long AI runs or big batches | n8n (not Starter) or Make Pro | Starter caps runs at 5 minutes and 5 concurrent; Make Free caps runs at 5 minutes |
| Must run inside Microsoft 365 | Power Automate | $15/user/mo (Premium, annual) — outside this skill's $0 scope; verify on Microsoft's pricing page |

## 4. n8n self-host setup (Community Edition)

Three routes, cheapest first. Node.js 20.19–24.x is required for the npm route (check with `node --version`).

### 4.1 Trial route — npx (5 minutes, nothing kept)

```bash
npx n8n
```

Open `http://localhost:5678`, create the owner account (email + password, stored locally in your instance). Stop with `Ctrl+C`. Data lives in `~/.n8n` and survives restarts on the same machine; the npx download itself is a throwaway — for a kept install use the global install or Docker below. (Tested 2026-11-23: `npx n8n` on Node v24.22.1; see TEST-LOG.md.)

### 4.2 Keeper route — Docker (recommended for anything beyond a trial)

```bash
docker pull n8nio/n8n
docker volume create n8n_data
docker run -d \
  --name n8n \
  -p 127.0.0.1:5678:5678 \
  -v n8n_data:/home/node/.n8n \
  -e N8N_HOST=localhost \
  -e N8N_PORT=5678 \
  -e GENERIC_TIMEZONE="Asia/Karachi" \
  n8nio/n8n
```

Open `http://localhost:5678`. The named volume keeps workflows, credentials and settings across restarts. Stop/start with `docker stop n8n` / `docker start n8n`. Never use `--rm` for a daily driver — it wipes the container (the volume survives, but do not rely on that).

### 4.3 Server route — Docker Compose + domain + HTTPS

For a public instance you need, at minimum: a VPS, a subdomain pointed at it, TLS (Traefik or Caddy in front of n8n), a strong owner password, and an encryption key you control (`N8N_ENCRYPTION_KEY`). This is a 30–45 minute job the first time and real server administration afterwards — updates, backups, log checks. If none of that is familiar, stay on the Docker route on your own machine, or pay for n8n Cloud. Do not expose a local instance to the public internet without authentication and HTTPS.

### 4.4 First-run checklist (every install)

- [ ] Owner account created; password stored in a password manager, not in a doc.
- [ ] Timezone set (`GENERIC_TIMEZONE`) so schedules fire when you expect.
- [ ] One test workflow runs end to end before any real credential is added.
- [ ] Backup: export workflows as JSON (workflow menu → Download) after every meaningful change; keep the exports in version control.

## 5. Build anatomy (every agent post)

1. **Problem + trigger** (what starts the workflow: schedule, webhook, new email, new row, new post).
2. **Tool map** (nodes/steps diagram — a custom diagram, not a fake screenshot).
3. **Step-by-step build** (numbered, with exact settings: trigger type, model, prompt, output destination).
4. **The agent prompt** (full 8-part block, §6).
5. **Test run** (what input, what output — labelled real or example).
6. **Limits + failure modes** (rate limits, task caps, self-hosting upkeep, hallucination risk).
7. **No-code alternative** (Zapier path where the lead build is n8n, and vice versa).

## 6. The agent prompt — full 8-part block

Every AI step in every build uses all eight parts. Write it out in full; a one-line prompt is a draft.

| # | Part | What goes here |
|---|---|---|
| 1 | **Role** | Who the agent is ("You are a research analyst who…") |
| 2 | **Context** | The situation, audience, and what good looks like |
| 3 | **Task** | The single job, in one sentence |
| 4 | **Inputs** | Exactly what data it receives, with field names |
| 5 | **Constraints** | Length, tone, what it must NOT do, what it must never invent |
| 6 | **Output structure** | The exact headings / JSON schema / table it must return |
| 7 | **Quality checks** | How it verifies its own output before returning it |
| 8 | **Failure behaviour** | What it returns when the input is missing, thin, or contradictory (never a confident guess) |

Template (copy and fill in):

```
ROLE: You are [role] for [audience].
CONTEXT: [situation in 2–3 sentences. What good looks like.]
TASK: [one sentence, one job.]
INPUTS: [field names and where they come from.]
CONSTRAINTS:
- [length / tone / format limit]
- Never invent a fact, figure, quote, or source. If the input does not contain it, say "not in the input".
- [domain rule, e.g. "no income claims, no guarantees"]
OUTPUT STRUCTURE:
[exact headings, or a JSON schema with field names and types]
QUALITY CHECKS (run before returning):
1. [check 1, e.g. "every claim traces to an input field"]
2. [check 2, e.g. "length within the limit"]
FAILURE BEHAVIOUR: If [input missing/thin/contradictory], return [exact fallback, e.g. "INSUFFICIENT INPUT: <what is missing>"] and nothing else.
```

## 7. Worked build 1 — Research agent

**Problem:** every week you need 3 fresh, verifiable topic ideas with sources — without opening 20 tabs.
**Trigger:** schedule, every Monday 08:00.
**Tool map:** Schedule Trigger → RSS Read → Code (dedupe + pick top 3) → AI step (draft briefs) → Set (format) → human review → publish.

### 7.1 Node-by-node (n8n)

| # | Node | Type | Exact settings |
|---|---|---|---|
| 1 | Schedule Trigger | `n8n-nodes-base.scheduleTrigger` | Rule: every week, Monday, 08:00 (your timezone, §4.4) |
| 2 | RSS Feed Read | `n8n-nodes-base.rssFeedRead` | URL: one feed per topic area (max 3 feeds — more feeds = more noise). Example: a vendor changelog or a topic RSS feed you already read |
| 3 | Pick Top 3 | `n8n-nodes-base.code` (JavaScript) | Dedupe by link, drop items older than 7 days, keep the 3 newest. See code below |
| 4 | Draft Briefs | `n8n-nodes-base.httpRequest` to your model provider's chat API (or the provider's own node) | POST, JSON body with the §6 prompt + the 3 items; API key from n8n credentials only, never pasted in the node |
| 5 | Format Brief | `n8n-nodes-base.set` | Fields: `title`, `hook`, `source_url`, `source_date`, `draft_status = "needs human review"` |
| 6 | Human review | Manual step, not a node | Read each brief, open each source, fix or drop anything unverified. Nothing publishes from this workflow automatically |

Code node (step 3) — paste exactly:

```javascript
// Dedupe by link, keep items from the last 7 days, keep the 3 newest.
const seen = new Set();
const cutoff = Date.now() - 7 * 24 * 60 * 60 * 1000;
const items = [];
for (const item of $input.all()) {
  const link = item.json.link || item.json.guid || '';
  const date = new Date(item.json.pubDate || item.json.isoDate || 0).getTime();
  if (!link || seen.has(link)) continue;
  if (date && date < cutoff) continue;
  seen.add(link);
  items.push(item);
}
items.sort((a, b) =>
  new Date(b.json.pubDate || 0) - new Date(a.json.pubDate || 0));
return items.slice(0, 3);
```

### 7.2 The agent prompt (step 4) — filled 8-part block

```
ROLE: You are a research analyst for a solo creator who publishes one practical AI tutorial a week.
CONTEXT: The reader is a beginner with no budget. They trust posts that name a source and a date, and they stop trusting posts that invent numbers.
TASK: Turn the 3 input items into 3 topic briefs.
INPUTS: title, link, pubDate, and description for each of the 3 items.
CONSTRAINTS:
- Each brief is 60–90 words.
- Every factual claim must come from the input item or its linked page summary. Never add a price, date, or feature the input does not state.
- No income claims, no guarantees, no "best ever" language.
- One call-to-action per brief, at the end.
OUTPUT STRUCTURE (repeat per brief):
**[Title]**
Hook: [one sentence]
Why now: [one sentence, with the source date]
Source: [link]
QUALITY CHECKS (run before returning):
1. Every date and number appears in the input.
2. Each brief is 60–90 words.
3. No claim without a source link.
FAILURE BEHAVIOUR: If fewer than 3 usable items arrive, return briefs only for the usable ones and add the line "INSUFFICIENT INPUT: <how many items arrived and why the rest were dropped>". Never invent a third topic.
```

### 7.3 Importable workflow JSON

The workflow above is shipped as `examples/research-agent-workflow.json` beside this skill (import: n8n → Workflows → … → Import from File). It contains nodes 1–3 and 5 plus a placeholder HTTP Request node for step 4 — add your own model credential before activating; the file never contains a key. Validate any hand-edited JSON with `python3 -m json.tool` before importing.

### 7.4 No-code alternative (Zapier / Make)

- **Zapier Free cannot run this as one Zap** — it allows two steps only (trigger + one action). The honest Free version is: RSS trigger → send yourself the raw items (one action), and you write the briefs. The full version needs Professional (multi-step) or the trial.
- **Make Free can run it:** RSS module → filter → AI module → Sheets module is 4 modules per run; at 1 run/week that is ~16 credits/mo, inside the 1,000-credit free tier. The binding limit is 2 active scenarios, not credits.

### 7.5 Test run (real, 2026-11-23)

Input: 20 real items fetched live from a public front-page feed (`https://hnrss.org/frontpage`, 23 Nov 2026 11:23 UTC). The Code node reduced them to the 3 newest; the AI step (Gemini 3 Flash Preview, free tier) returned 3 briefs, each 69–74 words (inside the 60–90 limit), every title and link matching the input, no invented facts, no guarantee language. Full log in TEST-LOG.md. The one failure found in testing: an RSS item with no `pubDate` was silently **dropped** by the date filter (its missing date parsed as 0, older than the 7-day cutoff). Fixed by the `date &&` guard in the code above, which keeps dateless items instead of dropping them; edge-case re-test green (dateless item kept, duplicate removed, 8-day-old item dropped). The same workflow was also imported and executed inside real n8n 2.48.8: RSS node fetched 20 items live and the Code node returned the same 3 — the run stops at the AI step with "Credentials not found", exactly as designed, because the shipped file carries a placeholder instead of a key.

## 8. Worked build 2 — Inbox triage agent

**Problem:** the inbox fills with newsletters, receipts, and real questions; only the questions need a human.
**Trigger:** new email (Gmail trigger / IMAP trigger) or schedule polling every 15 minutes.
**Flow:** Trigger → AI classify (question / newsletter / receipt / spam-risk) → IF question: draft a reply with the §6 prompt, save as draft, label `needs-human` → human reviews and sends. IF anything else: apply the matching label and archive. **Never auto-send.** The send step is always a human click.
**Zapier Free version:** trigger → single action (apply a label) only; classification needs a second step, so Free can only do "label everything from X". Full version needs Professional.
**Make Free version:** fits — Gmail watch → AI → router → label/archive is ~4 modules per email; 100 emails/mo ≈ 400 credits, inside Free.
**Failure mode to design for:** the classifier will mislabel. The safety is the label, not the model — a mislabelled question sits in `needs-human` for review instead of being auto-answered. Measure the mislabel rate on 20 real emails before trusting it.

## 9. Worked build 3 — Content repurposing agent (short)

**Problem:** one finished post should become three platform variants without rewriting from scratch.
**Trigger:** manual (you paste the finished post) or a new row in a tracker sheet.
**Flow:** Trigger → AI step with the §6 prompt ("rewrite for [platform], keep every fact, change only format and length") → Set (3 variants + a fact-check list) → human review → schedule.
**Rule:** the AI step receives the finished post as its ONLY source. If it adds a fact, a number, or a quote that is not in the input, the output fails the quality check and is rewritten by hand.

## 10. Error handling + cost guards

| Pattern | How | Why |
|---|---|---|
| Retry with backoff | n8n: node settings → Retry on fail (2 retries, wait 5s then 30s). Make: error handler route. Zapier: Autoreplay (paid) | Transient API failures are the commonest failure; a single attempt wastes the run |
| Dead-letter | Failed items go to a sheet/table with the error message + timestamp | You find out a workflow broke without opening the editor |
| Dedupe | Store processed IDs (link, message ID) in a sheet; skip any ID already seen | RSS and email triggers re-deliver; without dedupe you publish twice |
| Execution cap | n8n Cloud: watch the executions counter weekly. Zapier/Make: set the plan's usage alert the day you activate | Free tiers stop silently when exhausted — Zaps stop running at 100 tasks with no overage |
| Kill switch | One `active = false` toggle per workflow, written in the workflow's name or a control sheet | A runaway loop (e.g. a trigger that fires on its own output) is stopped in one click |
| Cost alert | Calendar reminder, weekly: open each tool's usage page and record executions/tasks/credits in the worksheet (§11) | A workflow that was cheap at 10 runs/day is not cheap at 1,000 |

**The loop rule:** a workflow must never trigger itself. If workflow A writes to a sheet that triggers workflow B which writes back to the same sheet, you have a loop. Break it with a "processed" flag or a separate output sheet.

## 11. Monthly cost worksheet (copy per workflow)

| Workflow | Tool + plan | Runs/mo (measured) | Units per run | Units/mo | Unit cost | $/mo | Cap / alert at |
|---|---|---|---|---|---|---|---|
| e.g. Research agent | n8n Cloud Starter | 4 | 1 execution | 4 | — | €20 flat | 2,000 executions |
| | | | | | | | |

Fill "Runs/mo (measured)" from the tool's usage page, never from a guess. If units/mo cross 80% of the plan allowance, decide before the month ends: cut runs, shorten the workflow, or upgrade — never let a silent stop be the way you find out.

## 12. Security checklist (run before any workflow goes live)

- [ ] Credentials live in the tool's credential vault only — never in a prompt, a node parameter, a doc, or a screenshot.
- [ ] Webhook URLs use authentication (header token or basic auth); a public webhook with no auth is a public endpoint.
- [ ] The AI step receives only the data the task needs — no passwords, no private client info, no full inboxes when a subject line would do.
- [ ] Data retention: know where the tool stores run history and for how long; delete runs containing personal data.
- [ ] Least privilege: each connected account uses the narrowest permission the workflow needs (read-only where possible; send-permission only on the account that sends).
- [ ] No auto-send, auto-post, or auto-pay without a human review step — until the workflow has run clean for 2 weeks.
- [ ] Exports backed up (workflow JSON + a note of which credentials it needs, never the secrets).

## 13. Limits + failure modes (say these out loud in every tutorial)

- **Hallucination:** the AI step will invent plausible facts. The defence is the §6 constraints + the human review gate, not a better model.
- **Free-tier ceilings:** Zapier Free stops at 100 tasks (no overage, Zaps stop). Make Free allows 2 scenarios and a 15-minute interval. n8n Starter caps runs at 5 minutes and 5 concurrent executions.
- **Self-hosting upkeep:** updates, backups, TLS renewal, and downtime are your job on Community Edition. Budget 1–2 hours a month.
- **Silent failures:** a schedule that stops firing looks identical to a week with no news. The dead-letter sheet (§10) and the weekly usage check are the detection.
- **Model changes:** free-tier model access changes without notice (a model that was free can move behind a paywall). The prompt block survives a model swap; the exact model name in a tutorial does not.

## 14. Test protocol (before you call a build done)

1. Run with real input, not lorem ipsum. Record input, output, and date.
2. Run twice with the same input. The output will differ (AI steps are non-deterministic) — the *structure* and the *facts* must not.
3. Break it once on purpose: empty input, malformed input, missing credential. Record what happens (the failure behaviour in §6 must fire, not a confident guess).
4. Check the cost: read the usage page after the test runs and record the units consumed.
5. Label the result: REAL RUN (with date and output) or BUILD GUIDE (not yet run end to end). Never upgrade a label without re-running.

## 15. How this skill compares

| Existing skill / resource | What it does | What this skill adds |
|---|---|---|
| Official n8n skills (`npx skills add n8n-io/skills`) | n8n node reference and build guidance | Beginner-first judgement: tool picker, billing-unit math, $0 path |
| czlonkowski/n8n-skills (14 skills, GitHub) | Production n8n via MCP: patterns, validation, self-hosting | Complete non-developer builds with full prompts, cost guards, and a no-code alternative per build |
| ericrisco/automation-flows | n8n/Make/Zapier builds with error paths; importable n8n JSON | The 8-part agent prompt block, the cost worksheet, and the test protocol |
| Cold-IQ n8n skill (GTM/sales) | n8n for B2B sales teams | General-purpose; not tied to one niche or one vendor's enrichment product |
| n8n-cli + 33 skills (GitHub) | Scriptable n8n REST API control | No-code-first; CLI is mentioned as an advanced path, not required |
| Zapier's official plugin / knowledge-work-plugins | Zapier actions from Claude | Tool-neutral picker — Zapier is one option, priced honestly against the other two |

Gap this skill closes: the existing skills assume you already picked a tool and know the nodes. This one starts one step earlier (which tool, what it really costs) and ends one step later (tested, guarded, costed).

## 16. Sources and what could not be verified

- Pricing: n8n.io/pricing, zapier.com/pricing, make.com/pricing; independent reads: CloudZero / JetAdmin / DEV (n8n, Sep–Nov 2026), Larksuite / Layer3Labs / GetOrchestra (Zapier, Sep–Oct 2026), JetAdmin / DEV (Make, Sep–Oct 2026). All figures re-checked 2026-11-23; re-check before quoting.
- Install: n8n docs (npm: Node.js 20.19–24.x; Docker: `n8nio/n8n` image, `http://localhost:5678`) via Linux Handbook and GetOrchestra guides, Oct 2026. npm route deprecation from n8n 3.0 is REPORTED (Oct 2026 guide), not confirmed from n8n's own docs — treat Docker as the keeper route regardless.
- Models: OpenAI ChatGPT pricing/help and Anthropic Claude pricing, Oct–Nov 2026 (Free/Plus/Pro figures in §2).
- Could not be verified (do not quote as fact): exact n8n Cloud overage pricing beyond the published plans; Zapier's per-step task cost for every AI/MCP step (varies by step — check the task history after a run); Make's per-module credit rate for AI/code modules (reported to differ from 1 credit — verify in your own usage page); any "average time saved" figure for any workflow.
