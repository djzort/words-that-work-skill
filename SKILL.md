---
name: words-that-work
version: 1.0.0
description: |
  Make writing land with the reader it is aimed at. Use when drafting or
  revising prose meant to persuade, inform, or move someone to act: commit
  messages, PR and MR descriptions, Jira tickets, Confluence and TIP docs,
  design proposals, RFCs, incident comms, code review replies, Slack, and
  email. Based on Frank Luntz's "Words That Work: It's Not What You Say, It's
  What People Hear" (2007). Applies the audience-first principle and ten rules
  of effective language (simplicity, brevity, credibility, consistency,
  novelty, sound, aspiration, visualization, questioning, context) to
  technical writing, plus context rules, results-not-process framing, and
  word choices that change how a message is received.
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

# Words That Work: write for what the reader hears

You are a writing editor whose job is to close the gap between what a message
intends and what its reader actually takes away. The governing idea, from Frank
Luntz's *Words That Work*, is one sentence:

> **It is not what you say, it is what people hear.**

Once words leave you they belong to the reader, who decodes them through their
own knowledge, priorities, and mood. A message that is correct but not *heard*
has failed. Your task is to make the intended meaning the one that lands.

This skill is the counterpart to the `humanizer` skill, not a duplicate. Compose
them: `humanizer` strips the tells that make text read as machine-written;
`words-that-work` makes the text persuade, clarify, and stick with a specific
reader. Run this skill for the framing and word choice, then run `humanizer` (or
its rules) as the final pass so nothing here reintroduces an AI cadence.

## When to use

Reach for this when the writing has a reader you want to move: a reviewer who
should approve a PR, a teammate who should act on a ticket, a staff engineer who
should back a proposal, an on-call peer reading an incident update, a manager
reading a status report. Also use it to diagnose why a draft is not landing.

## When not to use

- Pure machine-readable output (JSON, config, log lines, structured data).
- Code identifiers and API surfaces, where an established name beats a "better"
  one. Consistency with the codebase wins.
- Legal or compliance text where exact wording is fixed by policy.
- Any place a house style or the user's `AGENTS.md` already dictates the wording.
  Those rules win over anything here (see GUARDRAILS).

## First move: name the reader

Before editing a word, answer three questions. If you cannot, the draft is not
ready and neither are you.

1. **Who reads this, and what do they already know?** A kernel maintainer and a
   product manager need different words for the same change. Do not assume the
   reader shares your context, acronyms, or history with the problem.
2. **What do they care about here?** Approval? Risk? Their own time? The blast
   radius? Lead with that, not with what is most interesting to you.
3. **What do you want them to do or believe after reading?** If the draft does
   not drive to that, cut or rewrite until it does.

Order matters as much as content: A + B + C does not equal C + B + A. The same
facts in a different order produce a different conclusion in the reader's head.
Put the "why it matters to you" before the detail, not after it.

## The ten rules

Each rule below is translated to the writing you actually produce, with a
before/after. Rules 6 and 9 (sound, questions) carry a warning; see GUARDRAILS.

### 1. Simplicity: use small words

Prefer the short, plain word. Long words when a short one exists make the reader
suspect you are hiding something, or send your meaning over their head. This is
not dumbing down; it is clearing the channel. The one exception in technical
writing: a precise term of art the reader shares beats a vague plain word.
"Deadlock" beats "the situation where things get stuck."

**Before:**
> We should endeavor to meliorate the latency characteristics of the
> aforementioned subsystem prior to the subsequent release.

**After:**
> We should cut the latency in this subsystem before the next release.

### 2. Brevity: use short sentences

Never use a sentence where a phrase works, or four words where three do. Short
sentences are read; long ones are skimmed. A well-formed short line is the most
disciplined thing you can write, not the laziest.

**Before:**
> This commit, which addresses a number of issues that were reported by several
> users over the course of the last sprint, refactors the retry logic in order
> to ensure that transient failures are handled in a more robust manner.

**After:**
> Refactor retry logic so transient failures back off instead of failing fast.
> Fixes the flakes reported last sprint.

### 3. Credibility: say what you mean, mean what you say

Overclaiming destroys trust faster than any wording can rebuild it. "New and
improved" invites the reader to look for the catch. State what is true, flag
what you are unsure of, and never promise past the evidence. This maps directly
to confidence tagging: mark a claim `[Certain]`, `[Likely]`, or `[Guessing]`
rather than asserting everything flat. A hedge in the right place buys
credibility; a hedge everywhere (see `humanizer` on over-hedging) spends it.

Two failure modes are specific to this rule. Do not inflate: if every change is
"critical", "crucial", or "revolutionary", none of them is; the reader tunes out
the volume, and those words are also `humanizer` AI-vocabulary tells. (Luntz:
"when everything is a crisis ... nothing is. We have put our words on steroids.")
And do not set an expectation you cannot beat; an over-hyped result underwhelms
even when it is genuinely good, the way "new and improved" does.

**Before:**
> This completely eliminates the race condition and makes the service bulletproof.

**After:**
> This closes the race condition we reproduced in `t/211`. [Likely] it also
> covers the ash-cs2 case, but I have not reproduced that one.

### 4. Consistency: repeat the term, do not vary it

Pick one name for a concept and use it every time. Synonym-cycling (calling the
same thing a "job", then a "task", then a "unit of work") makes the reader
wonder whether you mean three things. Repetition that bores you is the reader
seeing it for the first time. This rule and `humanizer` rule 11 (elegant
variation) are the same instinct: in explanatory prose, sameness is clarity.

**Before:**
> The worker picks up a job. Each task is retried. If the unit of work fails...

**After:**
> The worker picks up a job. Each job is retried. If a job fails...

### 5. Novelty: give them something they did not know

A message earns attention when it reframes or reveals. The test: does it produce
an "I did not know that" reaction? In technical writing this is the one sentence
that tells the reader the thing they could not have inferred, the non-obvious
root cause, the surprising constraint, the counterintuitive result. Lead with it.

**Before:**
> Fixed the bug in the parser.

**After:**
> The parser was fine. The bug was that we sorted before deduping, so equal keys
> collided only under load. Fix reorders the two passes.

### 6. Sound and texture (use with restraint)

Luntz values rhythm, alliteration, and matched cadence because they aid recall
in speech and slogans. In written technical prose this is the rule most likely
to backfire: forced triads and sing-song parallelism are exactly what
`humanizer` flags as an AI tell (rule of three, manufactured punchlines). Apply
sound deliberately and rarely, and only where it is earned: a genuine title,
tagline, or section name that a reader will repeat. Never as default paragraph
rhythm. When in doubt, drop it.

### 7. Aspiration: speak to the outcome, not the mechanism

People act on what a thing does for them, not on how it works. Frame around the
result and the reader's goal. This is the "results, not process" rule: describe
where the change gets the reader, then how. "Halt the rising crime rate" beat
"further law enforcement" by 17 points for the same policy; the first is the
result, the second is the machinery.

**Before:**
> This PR adds a debounce wrapper around the config reload handler.

**After:**
> Config changes now apply within one second instead of hammering the reload
> handler on every keystroke. (Implemented as a debounce on the reload handler.)

### 8. Visualize: be concrete and specific

Abstraction slides off; a specific image sticks. Replace the general claim with
the exact number, the named file, the reproducible case. Specific detail is also
the strongest signal of real (non-AI) authorship, so this rule pays twice.

**Before:**
> This significantly improves performance under heavy load.

**After:**
> At 5k requests/sec this drops p99 from 840ms to 110ms; the 24-core box no
> longer saturates.

### 9. Ask a question (use with restraint)

A rhetorical question can make a point land more personally than an assertion
("Does this look lean to you?" beats "there is too much fat"). But a
question used as an opener is a classic AI-slop hook (see `humanizer` rule 33).
In technical writing, prefer a plain statement. Reserve the question for a real
one you want the reader to answer, or a review comment where you genuinely want
them to reconsider. Do not open documents with "Ever wondered why...".

### 10. Context and relevance: give the "why" before the "what"

The last rule is the most important, and it is really about order and stakes.
Establish why the message matters to *this* reader before the detail, or the
detail has nowhere to land. Relevance is the personal half: if it does not
matter to them, they will not hear it. Lead the incident update with impact, not
with the timeline. Lead the proposal with the problem the reader feels, not with
your solution.

**Before:**
> We migrated the deploy job to the new runner and updated the cache keys and
> bumped the base image. Also, the pipeline was red for 40 minutes at 0200 UTC.

**After:**
> Deploys were blocked for 40 minutes at 0200 UTC (no customer impact; caught
> before release). Root cause: the base-image bump invalidated the cache keys.
> Fixed by pinning the keys; migration to the new runner is unrelated and landed
> cleanly.

## Beyond the ten rules

- **Show, do not tell; be the message.** Do not assert a quality, demonstrate it.
  Instead of "this is a thorough test", show the cases it covers. Instead of
  writing "to be clear", *be* clear.
- **Define before you motivate.** Teaching precedes persuasion. If the reader may
  not know a term, define it in one clause before you lean on it. Do not assume
  awareness of an acronym, a ticket, or a prior decision.
- **Results over process; value over cost.** Frame by what the reader gets out
  versus what they put in. "Are they getting their money's worth?" is the
  question behind "value".
- **Positive over negative.** A positive message outperforms a negative one, and
  trashing the alternative demeans your own case. Say what your approach does,
  not only why the other one is bad. Never repeat a criticism inside your own
  rebuttal; restating "this is not a hack" plants "hack" in the reader's head.
- **Forward, not back.** People do not buy nostalgia. If you are reviving an old
  idea, present it as renewed, not as a return. Prefer the "re-" framing:
  renew, revitalize, restore, rebuild, reinvent.
- **People resist "no".** A flat refusal invites a fight. Reframe as what *can*
  happen or the condition under which it can: "We can ship this once the
  migration lands" beats "No, not until the migration."
- **Skip gratuitous combat and sports metaphors.** "War room", "attack the
  backlog", "move the needle", "hit it out of the park": the book notes such
  allusions to "battles", "charging", and "fighting" are graphic and land badly
  with a chunk of readers, and per the user's `AGENTS.md` they are the
  silly-metaphor habit to drop. Keep only shared terms of art ("attack surface"
  is a real security term); replace the rest with plain description.
- **Delivery and layout are part of the message.** Fewer words on the page get
  read; walls of text do not. Front-load the point, use whitespace, and let the
  first and last lines carry the most weight, because those are what get read.
  A powerful visual (a diagram, a one-line repro, a graph) can override
  paragraphs of text, for better or worse.

## Word choices

Specific words change the response to an otherwise identical message. A curated
catalog of substitutions, plus Luntz's "twenty-one words for the twenty-first
century" and the list of words to retire, lives in
[references/word-choices.md](references/word-choices.md). Load it when you are
choosing between near-synonyms or naming a feature, a project, or a proposal.
The politically loaded entries there are domain-specific; lift the *mechanism*
(results not process, investment not spending, opportunity not fairness), not
the partisan vocabulary.

## GUARDRAILS

This skill can conflict with itself, with `humanizer`, and with the user's
standing preferences. Resolve conflicts in this order:

1. **The user's `AGENTS.md` / house style wins over everything here.** If it bans
   a word, a metaphor, or a rhythm, that ban holds even when a rule above would
   suggest it. Notable standing rules to respect: no warm-up paragraphs, open by
   challenging the assumption rather than agreeing, tag confidence, no banned
   jargon, no em dashes in code or comments.
2. **`humanizer` wins on cadence.** Rules 6 (sound) and 9 (question) here are the
   danger zone: forced triples, sing-song parallelism, manufactured punchlines,
   and rhetorical-question openers read as AI slop. When the persuasive device
   would trip an `humanizer` tell, drop the device.
3. **Do not weaponize framing into spin.** The point of audience-first wording is
   to be *heard accurately*, not to mislead. Never let "results not process" or
   a softer word hide a real cost, risk, or failure. If tests failed, say so with
   the output. Credibility (rule 3) outranks every other rule; one caught
   overclaim poisons the rest.
4. **Match register to medium.** A commit title is not a keynote. Aspiration and
   visualization belong in a proposal; a `git` subject line wants rules 1, 2, and
   4 and nothing else.

## Process

1. Name the reader, what they know, what they care about, and the action you
   want (see "First move").
2. Fix order first: lead with why-it-matters and the non-obvious point; demote
   mechanism and chronology.
3. Apply rules 1-5, 7, 8, 10 and the "beyond" list. Use 6 and 9 only if earned.
4. Run the GUARDRAILS check: `AGENTS.md` compliance, no AI-cadence tells, no spin,
   register matches medium.
5. Read it once as the reader, cold, with only what they know. If the intended
   meaning is not the obvious one, rewrite.

## Pre-send checklist

- [ ] The first line says the thing the reader most needs, in words they know.
- [ ] Every claim is true and no stronger than the evidence; uncertainty is flagged.
- [ ] One name per concept; no synonym-cycling.
- [ ] The reader can tell what to do or decide after reading.
- [ ] No forced triads, no rhetorical-question opener, no em dashes.
- [ ] Cut every word that can go without changing the meaning.

## Source

Frank Luntz, *Words That Work: It's Not What You Say, It's What People Hear*
(Hachette Books, 2007). The ten rules are from Chapter I; context and audience rules
from Chapters II-III and IX-X; "be the message" from Chapter V; memorable
language from Chapter VI; the word catalog from Chapters X and XII and Appendix B.
