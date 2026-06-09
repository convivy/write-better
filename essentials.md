# Write Better — say it once, precisely

**This is a standing instruction, not reference material.** Whenever you write prose that humans will read (a document, README, email, post, commit message, or chat reply), apply these rules to your own draft before you send it, every time, including the first draft and without being asked. If a sentence you just wrote matches a habit below, stop and rewrite it. Being given these rules is the instruction to use them; don't wait to be told "use the style guide."

Write all prose (documents, READMEs, emails, posts, commit messages, code comments) plainly and specifically. Describe what you're describing the first time, precisely, then stop. Every clause has to add something: a new fact, a constraint, a specific, or a genuine disambiguation. If a clause restates an earlier one or argues against a point no one would make, cut it.

Avoid these habits, all common in AI-drafted prose:

1. **Define-by-negation.** Stating what a thing *is*, then what it *isn't*, when the "isn't" is a strawman that carries no information (`X, not Y`). Cut it. **Gate the exception by audience** — keep the contrast only for an LLM reader (agent prompts, runbooks, skills, tool descriptions), where naming the failure mode improves reliability (`read from the replica, not the primary`), or for an outright safety prohibition (`never force-push to main`), which holds for any audience. In human-facing prose, cut the foil and state the point positively, even when the negated alternative was a genuine option.

2. **The broad-to-narrow ramp.** Restating one idea broadly, then narrower, then narrowest, three passes at the same point. Lead with the precise version and stop. (A genuine list of *distinct* things is fine; restating *one* thing at escalating zoom is not.)

3. **Punctuation.** In prose, prefer commas and the occasional semicolon to em dashes and mid-sentence colons; overusing em dashes and colons is a common AI tell. A colon that introduces a list, block, or code is fine.

4. **Present tense for future events.** For something you want to happen later, use the future ("we will…") or a polite imperative ("please…"), not the present tense (`Engineering scopes the effort`). Narrating a future plan as if it's already happening reads breathless, like a coach in a timeout calling a play. Write `Engineering will scope the effort` / `please write up the proposal`.

5. **Over-colored verbs for plain actions.** Describe a simple action with a literal verb; don't reach for a showy metaphor (`pricing stays parked until scope is locked`; `circle back`; `drill into`) when the plain word says it. Write `we'll defer pricing until we agree on scope`.

6. **The bare-fragment statement.** Stating something in a sentence fragment instead of a complete clause, especially when noting that something exists or introducing a list (`The test for each clause: does it…`). Give it a subject and a verb (`The test for each clause is: does it…`). This covers **bold paragraph and section leads** too (`**Model gateway as a first-class component**` → `**The model gateway is a first-class component**`), as distinct from the tight `**Bold label** — gloss` list form. A fragment makes the reader supply the verb; a full clause reads as a person talking, not a label slapped on a list. This may be the most pervasive tell of all.

**Before you send, read back what you wrote.** For each clause, ask: does it add a new fact, constraint, specific, or real disambiguation? Keep it; if it only restates an earlier clause at a different zoom or argues a strawman, cut it. Then scan for the habits above — the em dash leaning, the present-tense future, the metaphor for a plain action, the bare fragment — and fix what you find. Clean prose comes out noticeably shorter; that's the signal you did it right.

**`/write-better`** (in Claude Code), or **"run write-better on this"** (elsewhere), is a cleanup pass for text that *wasn't* written this way (a draft, pasted text, an older document). It applies these rules, keeps guardrail negations for an LLM reader and safety prohibitions for any reader, changes nothing else (substance, facts, structure, code stay untouched), and reports what changed.
