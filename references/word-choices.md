# Word choices and craft rules

Load this when choosing between near-synonyms, naming a feature or proposal, or
tightening prose. It backs the "Word choices" and "Beyond the ten rules"
sections of `SKILL.md`.

The through-line from Luntz: **the label you give a thing often decides how it is
received.** "Change the name and you change the fortunes." A message and its
opposite can both be built from true statements; the wording picks which one the
reader hears. Use that power to be *heard accurately*, never to hide a cost. See
GUARDRAILS in `SKILL.md`.

---

## 1. Durable, non-partisan mechanisms

These transfer to any writing, including engineering and business prose. Apply
them directly.

- **Results, not process.** Name where the change gets the reader before how it
  works. "Halt the rising crime rate" beat "further law enforcement" by 17 points
  for identical policy. Engineering form: "cut p99 to 110ms" beats "added a
  debounce".
- **Value, not cost.** Frame as what the reader gets out versus what they put in.
  The question behind "value" is "are they getting their money's worth?"
- **Investment, not spending.** "Spending" implies waste and is gone; "investment"
  implies a responsible outlay that returns. Worth roughly a 10-point swing in
  support for the same line item. Use for time and effort too: "invest a day in
  the test harness" versus "spend a day".
- **Opportunity, over fairness or ownership.** "Opportunity" is expansive and
  alienates no one; it beats process-framings and outcome-framings alike.
- **Personalize the number.** Use the smallest denominator, per individual,
  anchored to an everyday cost. A week's premium framed as "a coffee a day"
  lands; abstract billions and percentages do not. Engineering form: "this saves
  each on-call engineer about 20 minutes per page" beats "reduces MTTR by 14%".
- **Certified, not attested.** "Certification" implies a process was followed and
  a guarantee given; a bare "guarantee" or "attested" implies neither.
- **Efficiency, not conservation.** "Efficiency" means more for less and reads as
  innovation; "conservation" reads as sacrifice and paying more to get less.
- **The right to choose, not the choice.** People want the right without the
  burden. Framing an option as a right adds intensity; framing it as a chore they
  must now perform adds friction.
- **Not-give, not deny.** "Deny" implies withholding an entitlement and slams a
  door; "not give" reads as opting out. The same policy polled 38 percent
  ("denied") versus 55 percent ("should not be given").
- **Accountability / responsibility, not transparency.** Most readers cannot
  define "transparency"; "responsibility" reads as good citizenship, and
  "accountability" implies enforcement.
- **American, not domestic.** "Domestic" is accounting jargon; the plain,
  human-scale word carries pride. Generalize: prefer the human word over the
  ledger word.
- **Recognizable, pronounceable, repeatable names.** A name a reader cannot say
  or spell cannot spread. "Wynn Resorts" replaced "Le Reve" for exactly this.
  Applies to project and feature names: pick what a teammate can repeat in
  standup.
- **Jargon to plain (safe swaps):** provider -> deliverer; interpretation ->
  analysis; comprehensive -> easy to understand; codes of conduct -> internal
  controls; breadth of services -> back to basics. The rule under all of these:
  swap the abstract institutional word for the concrete active one.

## 2. Luntz's twenty-one words for the twenty-first century

From Chapter XII. Each is a positive, aspirational, self-defined word. Lift the
ones that fit; most work in business writing, a few are domain-specific
(patient-centered, casual elegance).

`imagine`, `hassle-free`, `lifestyle`, `accountability`, `results` / `can-do
spirit`, `innovation`, the `re-` words (`renew, revitalize, rejuvenate, restore,
rekindle, reinvent`), `efficient` / `efficiency`, `the right to`,
`patient-centered`, `investment`, `casual elegance`, `independent`, `peace of
mind`, `certified`, `all-American`, `prosperity`, `spirituality`, `financial
security`, `a balanced approach`, `a culture of`.

Two with a warning:
- **`accountability` in a sales/reassurance context can backfire.** "We hold
  ourselves accountable" makes the reader ask "accountable for what?" and plants
  the failure. Prefer a plain declarative: "We deliver."
- **`a culture of ...` is a slam.** It is nearly always used to tar the whole of
  something ("culture of corruption"). Use it knowingly, rarely, and never to be
  unfair.

## 3. Domain-specific renamings: illustrations, not prescriptions

WARNING. The pairs below are deliberate political spin. Many trade accuracy for
emotional loading, which violates the credibility rule (Rule 3) and the anti-spin
guardrail. They are here to show *that a label moves the response*, not to be
copied. Do not use these to soften a real cost, risk, or failure. When you catch
yourself reaching for one, name the underlying mechanism instead (label sets
perception, results not process, human word over ledger word) and choose an
honest wording.

- estate/inheritance tax -> "death tax" (labels the trigger event)
- tax cuts -> "tax relief"; tax reform -> "tax simplification"
- government -> "Washington" (localizes blame)
- privatization -> "personalization"; private accounts -> "personal accounts"
- globalization / capitalism -> "free market economy"
- entrepreneur -> "small business owner"
- foreign trade -> "international trade"
- drilling for oil -> "exploring for energy"
- undocumented workers -> "illegal immigrants"; immigration reform -> "border security"
- tort reform -> "lawsuit abuse reform"; trial lawyer -> "personal injury lawyer"
- school choice -> "parental choice"; vouchers -> "opportunity scholarships"
- wiretapping -> "electronic intercepts"
- gambling -> "gaming"; liquor -> "spirits"
- bank -> "credit union"; customer -> "member"
- Social Security reform -> "strengthening Social Security"
- conservation -> "efficiency"; alternative energy -> "renewable energy"

The one durable rule inside all of these: **do not adopt your opponent's word.**
Using their vocabulary accepts their definitions and their conclusions. Whoever
defines the terms of the debate tends to win it. In a design review, if you argue
inside the framing of the proposal you dislike, you have half-lost already.

## 4. Prose-craft rules (generalizable)

From the letter-writing and case-study chapters. These apply to any written
piece.

- **Front-load and end-load.** Readers consume the first and last items and skim
  the middle. Put the highest-priority point first; put a human, memorable line
  last. In email, the P.S. is the second-most-read element.
- **One idea per message.** The "unique selling proposition" discipline. If a
  ticket or PR has one thing the reader must take away, do not bury it under
  three others.
- **Open with a single authoritative sentence.** "Everything you need to say
  should be up front; all that you want to say can come later."
- **Short sentences, short paragraphs.** "If your sentence has more than two
  commas, you have too many." Many short sentences beat a few long ones. Not
  meandering, not adjective-clotted.
- **Enumerate to show substance.** Numbered lists read as comprehensive and are
  more memorable than the same points in flowing prose. Three worked examples
  confer credibility.
- **Structure for the darting eye.** Bold, italics, and numbering pull the eye to
  what matters. Readers do not go top to bottom; they land on what stands out, so
  make what stands out the point.
- **Silence reads as guilt.** In a review thread or an incident channel, an
  unanswered objection is assumed correct. "A charge made is a charge believed
  unless and until refuted." Respond promptly and in writing.
- **First-mover advantage.** The argument made first sets the frame. Get your
  reasoning out before the alternative is framed for you.
- **Written beats verbal for credibility, and speed of response builds it.** Put
  positions in writing; a fast, thorough reply is itself persuasive.
- **Describe and quantify the problem; do not fight over its label.** Arguing
  whether something is a "crisis" or merely a "problem" is a trap. Show the
  impact with numbers and let the reader weigh it.
- **Show, do not tell.** Demonstrate the quality instead of asserting it. Do not
  write "to be clear"; be clear.
- **Everyday-request tactics (email, Slack, favors):** create empathy so the
  reader pictures your position; tie the ask to a genuine reason that matters to
  them; keep it to about four sentences; bracket a request with "please". When
  you are in the wrong, acknowledge it fully and up front, then ask; arguing
  makes the other side dig in.

## Source

Frank Luntz, *Words That Work* (Hachette Books, 2007), Chapters VII, VIII, X, XI,
XII and Appendix B.
