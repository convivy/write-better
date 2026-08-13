# Write Better — the style guide

Rules that keep Claude's prose plain, specific, and human. They name the habits common in AI-drafted writing, such as padding, hedging, and restating, and give the plainer form to use instead.

Use this as a standing reference: point Claude at it when you're writing or editing anything that matters (documents, READMEs, emails, posts, commit messages, code comments). The short version that travels in your always-on instructions is in `essentials.md`; this file is the full catalog. To clean up a specific document on demand, run `/write-better` (see [On command](#on-command-write-better) below).

---

## The core principle

**Say it once, precisely.** Describe what you're describing, the first time, precisely, then stop. Every clause has to earn its place by adding new information: a new fact, a constraint, a specific, or a genuine disambiguation. If a clause restates something already said, or argues against a point no one would make, cut it.

Expect prose written this way to come out noticeably shorter. That's the point.

---

## Write for the person who has to act

The rules below are about the prose. This one is about the reader.

**A document someone must approve is addressed to whoever has to say yes.** If they cannot reason
about what they are agreeing to, their approval is not an approval:

> A human approving a non-human-readable ADR means nothing. — Jay

The document that prompted this diagnosed a real defect, quoted every constant with its file and
line, and carried a supersession table and a per-slice test plan. All of it was written for the
coder. The person who had to approve it could not follow it.

**The test is whether the human's decision depends on parsing THAT text.** A PR body fails it even
though a person merges the PR, because the merge turns on the review verdict and the diff. Where a
human must parse the text to decide, the rule applies however many machines read it first.

### The ask is where it fails, and the author cannot see it

The labels feel meaningful to whoever assigned them:

✂️ **Cut** — quoted whole, because all three buttons fail and a shortened version hides that:

> Approve this: build Slice 1 (the smoke-gated harness) and run Slice 2's experiments E1 through
> E5 now, with Slices 3 through 5 pre-approved to ship as specified once Jay picks
> SEED_RANK_WINDOW and the Decision 3 branch from Slice 2's report. Approving takes Q1 through Q4
> as recommended and adopts the supersession table above, including carrying ADR-0117's Decisions
> 4, 6 and 7. Redirect for a different sweep, an affinity term designed now, the damp ahead of
> ADR-0109 Decision 3, or an untrusted-metric fast path. Deny to hold seed work and build ADR-0110
> as accepted first, against rosters this measurement says are half noise.

Every noun is a pointer, and the person who wrote the software could not follow it. Redirect names
four alternatives by label alone; Deny turns on a document the reader would have to go read.

✅ **Keep:**
> Approve this: no taste weighting goes into the draw until a measurement says it is needed.

If the commitment cannot be said in words, it is not yet a decision.

### Keep the numbers, cut the citations

Figures are what make a design believable, so they survive: *9,689 candidate artists*, *an
intruder scoring 0.17 while a real scene-mate sat at 0.74*. What goes is `seeds.py:453`, constant
names, and cross-reference chains. Name another record only where the reader needs to know its
fate. Implementation detail goes to the build plan, under a one-line pointer.

**Never bolt a plain-English summary onto a dense document.** The dense document is still the
thing being approved.

### The shape that works

What's broken, in the words a person would say out loud. The fix, in the same register. **The
catch** — where the fix falls short and what is unmeasured, which readers need most and authors
omit most. What you're guessing, as a table. Then the ask, as commitments.

**The target is five minutes to read, and to argue with.** Arguing is the harder half, because a
reader who follows a document but cannot find its weak point has nothing to push back on.

---

## The rules

Rules are grouped by category. Each one states the rule, why it matters, a ✂️/✅ example, and any exception.

### A. Concision

#### A1 — No define-by-negation
**Rule:** State what a thing *is*. Don't follow it with a strawman of what it *isn't*.
**Why:** The negated foil carries no information when no one would have assumed it. It reads as padding and dilutes the point.

- ✂️ "We build what we know, not what a market study tells us to build."
- ✅ "We build what we know."

**Exception — gate the contrast by audience.** Keep the "X, not Y" contrast only when the reader is an LLM, or when the negation is an outright safety prohibition. An LLM reader (agent prompts, runbooks, skills, tool descriptions) measurably benefits from having the failure mode named, so an operational "do X, not Y" that steers an action earns its place there. A human reader gets nothing from the foil, and it reads as an AI tell. So human-facing prose keeps no contrast. State the point positively and cut the foil, even when the negated alternative was a genuine option you weighed.

Outright safety prohibitions sit outside the gate. "Do not delete the prod table" and "never force-push to main" are instructions, not the define-by-negation tell, so they stay for any audience; stripping them from a human runbook would remove a real safety fence.

- ✅ (LLM-facing) "Read from the replica, not the primary." (names the wrong default for an agent following the instruction)
- ✅ (any audience) "Never force-push to main." (a safety prohibition)
- ✂️ (human-facing) "The infra week is a bake-off, not a commitment to a framework." → ✅ "The infra week is a time-boxed bake-off." (the foil steers no action, so cut it, even though dropping the framework was a real choice)

#### A2 — No broad-to-narrow ramp
**Rule:** Lead with the precise version and stop. Don't state an idea broadly, then narrower, then narrowest, three passes at one point, each rewording the last.
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

#### B5 — Complete the clause, even for a bare statement
**Rule:** State things in a complete clause, not a sentence fragment, even when you're only noting that something exists or introducing a list. Give it a subject and a verb; "There are X" beats a bare "X:". This applies to **bold paragraph and section leads** too: a bold lead that opens a paragraph is a sentence, so it takes a subject and a verb.
**Why:** A fragment makes the reader supply the verb. A full clause reads as a person talking, not a label slapped on a list.

- ✂️ "Three pieces:"
- ✅ "There are three pieces:" (or, with a named subject, "The bundle has three pieces.")
- ✂️ "**Model gateway as a first-class component.**" (a bold lead with no verb)
- ✅ "**The model gateway is a first-class component.**"

**Note:** A bold paragraph lead is distinct from the `**Bold label** — gloss` definition-list form that E1 allows. The definition-list form is a tight label on a list item; a paragraph lead is a sentence, so it takes a verb.

### C. Clarity & precision

#### C1 — Make the dependency explicit, not "load-bearing"
**Rule:** Instead of labeling something "load-bearing" (or "critical", "key"), name the dependency: what uses it, as an input to which decision.
**Why:** The label says a dependency exists but hides its shape. The explicit version tells the reader what reads the thing and what breaks without it.

- ✂️ "The `region` field is load-bearing for billing."
- ✅ "The billing job reads each account's `region` field to pick the tax rate."

### D. Tone & voice

These three travel together. They're how to write about plans and next steps like a person, not like AI. The tell is prose that narrates a future plan in clipped, present-tense, over-energized fragments.

#### D1 — Propose actions; don't just narrate them
**Rule:** When you want people to do something, propose it. Use "Let's…", "I propose we…", or a direct "please…". Don't hand someone a bare label ("Next steps:") over a list of flat declaratives.
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
**Why:** The metaphor adds energy the action doesn't have, and it usually doesn't fit, since pricing isn't a car. It reads as trying too hard.

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

#### E2 — No empty adverbs
**Rule:** Cut adverbs that intensify or hedge without adding meaning: "really," "actually," "basically," "simply," "just," "truly," "literally," "genuinely," "honestly."
**Why:** They promise emphasis or candor but deliver neither. "Really very important" is not more important than "important"; "basically just a simple fix" is not simpler than "a simple fix." Each one the reader encounters erodes trust in the surrounding prose.

- ✂️ "This is really very important and basically just a simple fix."
- ✅ "This matters; the fix is one line."

**Cross-reference:** "Genuinely" and "honestly" also appear in talk-better's Performed Sincerity rule (T5) as a participant-level move, prefacing a judgment to signal credibility. The sentence-level deadweight form is this rule's domain; the conversational-frame move is T5's.

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

This is the check the adversarial review pass runs, one clause at a time.

---

## On command: write better

In Claude Code, type **`/write-better`** (optionally with a file or path) to run a focused edit that conforms a document to this guide and changes nothing else. On Claude.ai or Cowork, say **"run write-better on this"**. Run it in three stages:

1. **Fix** the rule violations above.
2. **Review as an adversary.** Re-read the fixed text as a critic who assumes at least one violation survived and means to catch it. Go rule by rule, then run the say-it-once test from [The test](#the-test) above, checking that every clause adds a new fact, constraint, or specific. For each check, quote a still-violating sentence, or clear that check by name. A blanket "looks clean" is a failed review; you clear a check only after reading for it.
3. **Rewrite** from the review, fixing or cutting every sentence it flagged.

Throughout, keep guardrail negations for an LLM reader and safety prohibitions for any audience (see A1); change nothing else, leaving substance, facts, numbers, steps, structure, headings, and code untouched; and report what changed as a short list, naming the rule each edit served.

In Claude Code, dispatch stage 2 to a separate reviewer subagent for a stronger pass. Expect a styled document to come out noticeably shorter.

---

## Adding a rule

Copy this template, fill it in, and slot it under the right category (give it the next number in that category, e.g. B6). Keep examples real and short.

```
#### <ID> — <short name>
**Rule:** <imperative, one line>
**Why:** <one line>

- ✂️ <bad example>
- ✅ <good example>

**Exception:** <when not to apply — omit if none>
```

---

## Changelog

- **2026-08-12 — "Write for the person who has to act" added.** A new principle-level section: a document someone must approve is addressed to that person, and an approval the reader cannot reason about is not an approval. It names where the failure concentrates (the closing approve/redirect/deny block, whose labels feel meaningful only to their author), what survives a rewrite (measured numbers) and what does not (file:line citations, cross-reference chains), and the five-part shape that works. Scoped to documents a human must act on; text written for a machine reader that no human approves is exempt. Prompted by an ADR that was technically correct and unreadable, and by Jay's ruling on it: "A human approving a non-human-readable ADR means nothing."
- **2026-07-10 — E2 promoted to the always-on surfaces.** essentials.md gains habit 7 (Empty adverbs) and the `/write-better` command and skill gain the matching core rule; E2 previously existed only in this catalog, and the enforcement passes in the other surfaces enumerate only their own listed habits/rules, so a first draft never checked it.
- **2026-07-10 — Three-pass protocol replaces the single read-back self-check.** essentials.md, the `/write-better` command, and the skill now run three distinct passes (draft, adversarial review, rewrite) instead of one combined self-check; the adversarial review pass assumes at least one violation survived and clears each check only after quoting or naming it; this document's own "On command" section was updated to run the say-it-once test in the adversarial review stage too.
- **2026-06-21 — E2 added (Empty adverbs).** New rule cutting "really," "actually," "basically," "simply," "just," "truly," "literally," "genuinely," "honestly" when they intensify or hedge without adding meaning. Cross-references talk-better's T5 (Performed sincerity), which owns the conversational-frame use of the same words.
- **2026-06-08 — A1 exception gated by audience.** The old "keep the contrast" exception fired whenever the negated alternative was "a real, likely-wrong choice," which was broad enough to wave through rhetorical foils in human-facing prose (the catching case: "a bake-off, not a commitment to a framework"). The exception now keeps "X, not Y" only for an LLM reader, where naming the failure mode improves reliability, or for an outright safety prohibition, which holds for any audience. Human-facing prose gets no exception.
- **2026-06-08 — B5 covers bold leads.** B5 now states that a bold paragraph or section lead is a sentence and takes a subject and a verb ("The model gateway is a first-class component", not the bare "Model gateway as a first-class component"), distinct from the `**Bold label** — gloss` definition-list form E1 allows.

---

*A free tool from Convivy. Use it, change it, pass it on.*
