# Write Better — the style guide

Rules that keep Claude's prose plain, specific, and human. They name the habits common in AI-drafted writing, such as padding, hedging, and restating, and give the plainer form to use instead.

Use this as a standing reference: point Claude at it when you're writing or editing anything that matters (documents, READMEs, emails, posts, commit messages, code comments). The short version that travels in your always-on instructions is in `essentials.md`; this file is the full catalog. To clean up a specific document on demand, run `/write-better` (see [On command](#on-command-write-better) below).

---

## The core principle

**Say it once, precisely.** Describe what you're describing, the first time, precisely — then stop. Every clause has to earn its place by adding new information: a new fact, a constraint, a specific, or a genuine disambiguation. If a clause restates something already said, or argues against a point no one would make, cut it.

Expect prose written this way to come out noticeably shorter. That's the point.

---

## The rules

Rules are grouped by category. Each one states the rule, why it matters, a ✂️/✅ example, and any exception.

### A. Concision

#### A1 — No define-by-negation
**Rule:** State what a thing *is*. Don't follow it with a strawman of what it *isn't*.
**Why:** The negated foil carries no information when no one would have assumed it. It reads as padding and dilutes the point.

- ✂️ "We build what we know, not what a market study tells us to build."
- ✅ "We build what we know."

**Exception — keep informative negation.** When the alternative is a *real, likely-wrong* choice, the contrast is a guardrail and carries information. Keep it. This matters most in technical and operational instructions, where an explicit "do **not** X" fences off a known failure.

- ✅ "Read from the replica, not the primary." (the primary is a tempting, wrong default)
- ✅ "Never deploy on a Friday."

#### A2 — No broad-to-narrow ramp
**Rule:** Lead with the precise version and stop. Don't state an idea broadly, then narrower, then narrowest — three passes at one point, each rewording the last.
**Why:** The restatements are redundancy. A reader anchors on the precise phrasing, and the earlier passes only delay it.

- ✂️ "We support teams — engineering teams, specifically — backend engineers, to be exact."
- ✅ "We support backend engineers."

It also shows up as padded appositive lists that zoom on one idea: "their data, their operational data, their whole system of record." A list of *distinct* things is fine; restating *one* thing at escalating zoom is not.

### B. Structure & flow

#### B1 — One idea per sentence
**Rule:** Put one sentence-sized idea in each sentence, and express each sentence-sized idea in one sentence.
**Why:** A reader parses a single-idea sentence in one pass, and finds a single-sentence idea exactly where it lives.

- ✂️ "The service indexes new records and re-indexes changed ones while skipping drafts, and it logs every action it takes."
- ✅ "The service indexes new records and re-indexes changed ones. It skips drafts. It logs every action."

#### B2 — Stitch sentences, end to start
**Rule:** End a sentence on the idea that opens the next one, so the closing noun becomes the next sentence's actor.
**Why:** The reader meets known information first and new information second, then follows the chain without re-anchoring.

- ✂️ "The scheduler starts the job. Each run gets a budget cap."
- ✅ "The scheduler starts the job. The job runs until it finishes or hits its budget cap."

#### B3 — Stitch paragraphs, end to start
**Rule:** When paragraphs build an arc, open each paragraph with the concept that closed the one before it.
**Why:** The B2 hand-off, applied at paragraph scale, carries the arc across the break.

#### B4 — Name the actor, and lead with it
**Rule:** Make the actor of a sentence explicit and lead with it, in subject-verb-object order.
**Why:** Subject-verb-object is the foundational English sentence structure. It grounds the reader by naming who acts before the details arrive, and prose that leans on it reads easily.

- ✂️ "The queue is drained each night."
- ✅ "The scheduler drains the queue each night."

### C. Clarity & precision

#### C1 — Make the dependency explicit, not "load-bearing"
**Rule:** Instead of labeling something "load-bearing" (or "critical", "key"), name the dependency: what uses it, as an input to which decision.
**Why:** The label says a dependency exists but hides its shape. The explicit version tells the reader what reads the thing and what breaks without it.

- ✂️ "The `region` field is load-bearing for billing."
- ✅ "The billing job reads each account's `region` field to pick the tax rate."

### D. Tone & voice

These three travel together: they're how to write about plans and next steps like a person, not like AI. The tell is prose that narrates a future plan in clipped, present-tense, over-energized fragments.

#### D1 — Propose actions; don't just narrate them
**Rule:** When you want people to do something, propose it — "Let's…", "I propose we…", or a direct "please…". Don't hand someone a bare label ("Next steps:") over a list of flat declaratives.
**Why:** A declarative states a fact, but a plan isn't a fact until people agree to it. Proposing it asks for the agreement the plan needs, and it reads as a person talking to people.

- ✂️ "Next steps: Sam and Alex build the proposal."
- ✅ "Let's take these as our next steps. Sam and Alex, please write up the proposal."

#### D2 — Future actions in the future tense or a polite imperative, not the present
**Rule:** For something you want to happen later, use the future ("we will…", subjunctive where it fits) or a polite imperative ("please scope…"). Don't narrate a future plan in the present tense.
**Why:** The present tense states a future plan as if it's already happening. It reads breathless, like a coach in a timeout calling a play, and leaning on it for everything stresses the reader.

- ✂️ "Engineering scopes the effort in parallel." (for work not yet started)
- ✅ "Engineering will scope the effort in parallel."
- ✂️ "Sam and Alex build the proposal."
- ✅ "Sam and Alex, please write up the proposal."

#### D3 — Don't over-color a plain action with a showy verb
**Rule:** Describe a simple action with a literal verb. Don't reach for a vivid metaphor ("stays parked", "is locked", "circle back", "drill into") when the plain word says it.
**Why:** The metaphor adds energy the action doesn't have, and it usually doesn't fit — pricing isn't a car. It reads as trying too hard.

- ✂️ "Pricing stays parked until scope is locked."
- ✅ "We'll defer pricing until we agree on the scope."

### E. Formatting & mechanics

#### E1 — Commas and semicolons over em dashes and colons
**Rule:** In flowing prose, join clauses with commas and the occasional semicolon, and avoid em dashes and mid-sentence colons.
**Why:** Em dashes and colons interrupt the line, and leaning on them (a common AI tell) makes prose choppy. Commas and semicolons keep it moving.

- ✂️ "The job started — but the queue was empty — so it skipped the run."
- ✅ "The job started, but the queue was empty, so it skipped the run."
- ✂️ "One thing was wrong: the queue was empty."
- ✅ "One thing was wrong, an empty queue."

**Exception:** A colon that introduces a list, block, or code is fine, and the `**Bold label** — gloss` definition-list dash is fine structure. This rule targets em dashes and colons dropped mid-sentence in flowing prose.

### F. Your own rules

This catalog is a starting point. Add categories and rules that fit your own writing, using the [template](#adding-a-rule) below.

---

## The test

For each clause, ask: **does this add new information?**

| Keep | Cut |
|------|-----|
| A new fact, constraint, number, or specific | A restatement of the previous clause at a different zoom |
| A real disambiguation that rules out a likely misreading | A strawman named only to sound definitive |

A topic sentence followed by *new* detail is good writing. A topic sentence followed by the same idea reworded is not.

---

## On command: write better

In Claude Code, type **`/write-better`** (optionally with a file or path) to run a focused edit that conforms a document to this guide and changes nothing else. On Claude.ai or Cowork, say **"run write-better on this"**. Either way, the pass is:

1. **Fix violations** of the rules above.
2. **Keep guardrail negations** — `do NOT X` / "read from the replica, not the primary" / "never deploy on a Friday," where the alternative is a real, likely-wrong choice or an operational rule. These carry information; stripping them removes a fence around a known failure. This matters most in technical instructions, runbooks, and code comments.
3. **Change nothing else.** Leave the substance, facts, numbers, steps, structure, headings, and code untouched. It's a style pass, not a rewrite — don't reorganize, don't add, don't "improve" wording beyond conforming to the guide.
4. **Report what changed** — a short list of the edits, so the pass is reviewable.

Expect a styled document to come out noticeably shorter.

---

## Adding a rule

Copy this template, fill it in, and slot it under the right category (give it the next number in that category, e.g. B5). Keep examples real and short.

```
#### <ID> — <short name>
**Rule:** <imperative, one line>
**Why:** <one line>

- ✂️ <bad example>
- ✅ <good example>

**Exception:** <when not to apply — omit if none>
```

---

*A free tool from Convivy. Use it, change it, pass it on.*
