---
name: prompt-writing
description: Teach one copy-ready AI prompt per post with a fixed 8-part block — role, context, task, inputs, constraints, output structure, quality checks — so a reader can run it without guessing.
version: 1.0.0
author: Muhammad Saad Ranjha (Beyond Muhammad Saad)
created: 2026-11-23
---

# Prompt Writing

## Purpose

Make every tutorial post teach the exact prompt — role, context, task, inputs, constraints, output structure, quality checks — so a reader can run the workflow without guessing. "Ask ChatGPT to do this" is incomplete and never ships.

## When to use

- Every tutorial post and any post that teaches an AI task, workflow, model, or use-case.
- Any post whose hook promises "do X with AI" — the prompt block is the proof of the promise.

## Rules (hard)

- **Every tutorial carries the full 8-part prompt block** (below). Missing any part = fail the quality gate.
- **Never promise a prompt produces perfect, accurate, or guaranteed results.** Always include a verification step for research, factual, and high-impact tasks.
- **Placeholders must be explained AND filled once.** A prompt with unexplained `[brackets]` is incomplete.
- **Expected output is labelled as an example if not actually generated.** Never present an invented output as a real result.
- **Limitations are visible, not buried:** where the output may fail, hallucinate, need human review, or expose sensitive data.
- **Protect user data:** never tell readers to paste passwords, private client info, personal records, or confidential business data into a tool without checking its data controls first.
- **One CTA per post.** The prompt itself is the save-worthy asset; the CTA asks for one action only.
- **Ask at most three clarifying questions before writing.** If the request is still vague after three, write the prompt for the most likely intent and say what you assumed.
- **Token-efficiency pass last.** Cut every word that does not change the output. The best prompt is the one where every word is load-bearing, not the longest one.

## The 8-part prompt block (non-negotiable)

1. **PROMPT TITLE** — name the result the reader will create.
2. **COPY-READY PROMPT** — the full prompt in a readable code/card block. Must contain: role · context · task · inputs · constraints · output structure · quality checks.
3. **PLACEHOLDERS** — every `[insert your details]` field explained, plus one filled example.
4. **RECOMMENDED TOOL/MODEL** — tool and model/mode if it materially affects the result; verify availability on the vendor's model list today — model names and availability change monthly, so never state them from memory.
5. **HOW TO USE** — numbered steps, including what files, URLs, screenshots, or context the user must provide.
6. **EXPECTED OUTPUT** — realistic example or excerpt, labelled as an example if not actually generated.
7. **ITERATION PROMPT** — a follow-up prompt to improve, verify, or refine the first result.
8. **LIMITATIONS** — where the output may fail, hallucinate, require human review, or expose sensitive data.

## Prompt-writing craft

- **Role first, task second, output format last.** The model needs to know who it is, what to do, and what "done" looks like — in that order.
- **Constraints beat adjectives.** "Under 120 words, 5 bullets, no jargon" beats "make it good".
- **Output structure is a contract:** headings, bullet counts, table columns, word limits — specified, not hoped for.
- **Quality checks inside the prompt:** "Flag any claim you cannot support from the sources I gave you" — build verification into the prompt, not just the post.
- **One prompt, one job.** If the workflow needs two jobs (research, then draft), write two prompts and number them.
- **Route to the tool.** A prompt for an image model needs comma-separated descriptors and a negative prompt; a prompt for a coding agent needs file scope and stop conditions; a prompt for a chat model needs role + output contract. One generic shape does not fit all three — name the target tool and shape the prompt to it.
- **Test the prompt once before publishing if possible;** if not tested, say so ("prompt drafted, not yet run — try it and tell us what it returned").

## Iteration prompts (keep a bank)

- Verify: "Check every factual claim in your answer against the sources I provided. List any claim you cannot support, and remove it."
- Tighten: "Cut this to half the length. Keep every number and every named tool. Remove filler."
- Reframe: "Rewrite this for [audience], at [reading level], keeping the same facts."
- Compare: "Give me 2 alternative versions: one shorter, one more detailed. Tell me which you recommend and why."

## Worked example — the full 8-part block, filled

### 1. PROMPT TITLE

Turn rough meeting notes into a client-ready follow-up email.

### 2. COPY-READY PROMPT

```
You are a professional account manager writing to a client after a project call.

Context: I pasted my raw meeting notes below. The client is [CLIENT NAME] and the project is [PROJECT NAME].

Task: Write a follow-up email that (1) thanks them for the call, (2) lists the decisions made, (3) lists the open items with an owner and a date for each, and (4) states the next step.

Inputs: my raw notes are in the [NOTES] section below.

Constraints:
- Under 180 words.
- Plain, professional English. No jargon, no superlatives, no exclamation marks.
- Do not invent decisions, dates, or owners. If a note is unclear, write "[confirm: ...]" instead of guessing.
- Use the names exactly as they appear in the notes.

Output structure:
- Subject line (one line, under 60 characters)
- Greeting
- One sentence thanking them
- "Decided:" followed by a bulleted list
- "Open items:" followed by a bulleted list, each item as "[item] — Owner: [name] — Due: [date]"
- One closing sentence stating the next step

Quality checks before you finish:
- Every decision and open item in your email must trace to a line in my notes. List any note line you could not use.
- Flag any date or owner you had to guess.

[NOTES]
[paste your raw meeting notes here]
```

### 3. PLACEHOLDERS

- `[CLIENT NAME]` — the client or company name, e.g. "Northwind Retail".
- `[PROJECT NAME]` — the project, e.g. "website redesign".
- `[NOTES]` — your raw notes, pasted verbatim. Filled example: "Call with Sara (Northwind). Decided: homepage copy approved. Open: pricing page mockup — Sara to send by Friday. Next: review call Monday 10am."

### 4. RECOMMENDED TOOL/MODEL

Any general chat model (ChatGPT, Claude, Gemini). No special mode needed. Verify the model name you recommend on the vendor's model list on the day you publish — model names change monthly.

### 5. HOW TO USE

1. Copy the prompt block above.
2. Replace `[CLIENT NAME]`, `[PROJECT NAME]`, and `[NOTES]` with your details.
3. Paste into your chat model and run it once.
4. Read the "could not use" list at the end — fix any unclear note and re-run if needed.
5. Send only after you have checked every date and owner against your notes.

### 6. EXPECTED OUTPUT (example — generated by running this prompt on the sample notes in §3; see TEST-LOG.md)

> **Subject:** Follow-up: Northwind website redesign — decisions & next steps
>
> Hi Sara,
>
> Thank you for the call today.
>
> **Decided:**
> - Homepage copy approved.
>
> **Open items:**
> - Pricing page mockup — Owner: Sara — Due: Friday
>
> **Next step:** Review call on Monday at 10am.
>
> Best regards

### 7. ITERATION PROMPT

"Rewrite this email in a warmer tone, keeping every decision, owner, and date exactly the same. Do not add or remove any item."

### 8. LIMITATIONS

- The model can misread messy notes and turn a question ("should we approve?") into a decision. Always check the "Decided" list against your notes.
- Dates like "Friday" are ambiguous without a calendar date — add the date yourself before sending.
- Do not paste confidential client information into a tool whose data controls you have not checked.

## Visual treatment

- Prompt shown as a readable code-style block or clean prompt card. Minimum readable size on mobile; no tiny text.
- On carousels, the prompt gets its own slide(s) — never shrunk to fit beside other content.
- On video, the prompt appears on screen long enough to read or screenshot, and is repeated in the caption/description.

## Template (inline — copy per tutorial)

```markdown
## Tutorial — [title]
1. PROMPT TITLE: ...
2. COPY-READY PROMPT: ``` ... ```
3. PLACEHOLDERS: [field] — what it is + one filled example
4. RECOMMENDED TOOL/MODEL: ... (verified [date])
5. HOW TO USE: 1. ... 2. ... 3. ...
6. EXPECTED OUTPUT: [label: generated / example]
7. ITERATION PROMPT: "..."
8. LIMITATIONS: ...
Tested: yes [date, tool] / no — drafted, not yet run
```
