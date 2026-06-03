# Write Better — say it once, precisely

Write all prose (documents, READMEs, emails, posts, commit messages, code comments) plainly and specifically. Describe what you're describing the first time, precisely, then stop. Every clause has to add something: a new fact, a constraint, a specific, or a genuine disambiguation. If a clause restates an earlier one or argues against a point no one would make, cut it.

Avoid these habits, all common in AI-drafted prose:

1. **Define-by-negation.** Stating what a thing *is*, then what it *isn't*, when the "isn't" is a strawman that carries no information (`X, not Y`). Cut it. **Keep the informative kind** — where the alternative is a real, likely-wrong choice, the contrast is a guardrail (`read from the replica, not the primary`; `never deploy on a Friday`). Never strip operational "do **not**" constraints.

2. **The broad-to-narrow ramp.** Restating one idea broadly, then narrower, then narrowest, three passes at the same point. Lead with the precise version and stop. (A genuine list of *distinct* things is fine; restating *one* thing at escalating zoom is not.)

3. **Punctuation.** In prose, prefer commas and the occasional semicolon to em dashes and mid-sentence colons; overusing em dashes and colons is a common AI tell. A colon that introduces a list, block, or code is fine.

4. **Present tense for future events.** For something you want to happen later, use the future ("we will…") or a polite imperative ("please…"), not the present tense (`Engineering scopes the effort`). Narrating a future plan as if it's already happening reads breathless, like a coach in a timeout calling a play. Write `Engineering will scope the effort` / `please write up the proposal`.

5. **Over-colored verbs for plain actions.** Describe a simple action with a literal verb; don't reach for a showy metaphor (`pricing stays parked until scope is locked`; `circle back`; `drill into`) when the plain word says it. Write `we'll defer pricing until we agree on scope`.

The test for each clause: does it add a new fact, constraint, specific, or real disambiguation? Keep it. Is it a restatement at a different zoom, or a strawman? Cut it. Expect clean prose to come out noticeably shorter; that's the point.

**`/write-better`** (in Claude Code), or **"run write-better on this"** (elsewhere), means: apply these rules to the document, keep guardrail negations, change nothing else (substance, facts, structure, code stay untouched), and report what changed.
