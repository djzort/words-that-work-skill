---
name: words-that-work
version: 1.0.0
description: Make persuasive, audience-first technical writing land (PRs, proposals, tickets, incident comms). Applies audience-first framing and 10 language rules to technical prose.
license: MIT
compatibility: claude-code opencode
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
---

# Words That Work

Close the gap between intended meaning and reader takeaway: **It is not what you say, it is what people hear.**

Run this skill first for audience framing and word choice, then run `humanizer` as a final pass to ensure clean cadence.

## Applicability
* **Use for:** PR descriptions, Jira tickets, design proposals/RFCs, incident comms, code reviews, Slack/email asks.
* **Do not use for:** Code identifiers, machine-readable configs, legal text, or where house style (`AGENTS.md`) dictates wording.

## First Move: Audience & Order
Answer 3 questions before writing:
1. **Reader:** Who reads this, and what context/acronyms do they lack?
2. **Core Concern:** What do they care about (risk, approval, blast radius, time)?
3. **Outcome:** What specific action or belief do you want?

**Order Rule:** Put "why it matters to the reader" before details. Fact order dictates the conclusion (A + B + C ≠ C + B + A).

## The Ten Rules

### 1. Simplicity
Use plain words. Exception: Precise technical terms of art beat vague words (`"Deadlock"` > `"things get stuck"`).
* **Before:** We should endeavor to meliorate the latency characteristics of the aforementioned subsystem prior to the subsequent release.
* **After:** We should cut the latency in this subsystem before the next release.

### 2. Brevity
Use short sentences and phrases. Cut filler words.
* **Before:** This commit, which addresses a number of issues that were reported by several users over the course of the last sprint, refactors the retry logic in order to ensure that transient failures are handled in a more robust manner.
* **After:** Refactor retry logic so transient failures back off instead of failing fast. Fixes the flakes reported last sprint.

### 3. Credibility
State truth; tag confidence (`[Certain]`, `[Likely]`, `[Guessing]`). Never inflate (`"critical"`, `"revolutionary"`). Do not promise past evidence. A hedge in the right place builds trust; hedging everywhere destroys it.
* **Before:** This completely eliminates the race condition and makes the service bulletproof.
* **After:** Closes the race condition we reproduced in `t/211`. [Likely] it also covers the ash-cs2 case, but I have not reproduced that one.

### 4. Consistency
Use one name per concept. Avoid synonym-cycling (`job` -> `task` -> `unit of work`). Repetition that feels boring to you provides clarity to a first-time reader.
* **Before:** The worker picks up a job. Each task is retried. If the unit of work fails...
* **After:** The worker picks up a job. Each job is retried. If a job fails...

### 5. Novelty
Lead with the non-obvious root cause, constraint, or counterintuitive result.
* **Before:** Fixed the bug in the parser.
* **After:** Parser was fine; bug was sorting before deduping, causing key collisions under load. Fix reorders passes.

### 6. Sound & Cadence (Restraint)
Avoid forced triads or sing-song parallelism (triggers AI-slop detectors). Use only in section titles or taglines.
* **Rule:** Default to dropping manufactured rhythm.

### 7. Aspiration
Frame around outcomes/results, not machinery/process.
* **Before:** This PR adds a debounce wrapper around the config reload handler.
* **After:** Config changes now apply within one second instead of hammering the reload handler on every keystroke. (Implemented as a debounce.)

### 8. Visualize
Use concrete numbers, named files, and exact reproducible data.
* **Before:** This significantly improves performance under heavy load.
* **After:** At 5k req/sec, drops p99 from 840ms to 110ms; CPU no longer saturates.

### 9. Questions (Restraint)
Avoid rhetorical or question openers ("Ever wondered why..."). Use questions only for actual user feedback or code reviews.
* **Rule:** Prefer plain statement openers.

### 10. Context
Establish "why it matters" before "what happened".
* **Before:** Migrated deploy job, updated cache keys, bumped base image. Pipeline red for 40m at 0200 UTC.
* **After:** Deploys blocked 40m at 0200 UTC (no customer impact). Cause: base-image bump invalidated cache keys. Fixed by pinning keys.

## Actionable Craft Principles
* **Show, don't tell:** Demonstrate quality with evidence/test cases; never write "to be clear".
* **Define before motivating:** Explain unknown terms in one clause before using them.
* **Positive over negative:** State what your approach does; never repeat opposing criticisms in rebuttals.
* **Forward framing:** Use `re-` terms (`renew`, `rebuild`, `reinvent`).
* **Refuse softly:** Frame "no" as conditions under which it becomes "yes".
* **Drop combat metaphors:** Replace "war room" or "attack backlog" with plain description (except technical terms like "attack surface").
* **Layout:** Front-load points; use whitespace; format for scanning.

## Guardrails (Precedence Order)
1. **House style (`AGENTS.md`) wins** over all rules here.
2. **`humanizer` cadence wins:** Drop forced triads, rhetorical questions, em dashes.
3. **No spin:** Never hide costs, risks, or test failures. Credibility overrides framing.
4. **Match register:** Git commits = rules 1, 2, 4 only; proposals = aspiration & visualization.

## Pre-Send Checklist
- [ ] First line states what the reader needs in known words.
- [ ] Claims are true and uncertainty is tagged (`[Certain]`, `[Likely]`, `[Guessing]`).
- [ ] Single term per concept (no synonym-cycling).
- [ ] Clear required action/decision stated.
- [ ] No forced triads, no rhetorical openers, no em dashes.
- [ ] Zero redundant words.
