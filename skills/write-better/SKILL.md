---
name: write-better
description: Tighten prose to the Write Better style — say it once and precisely; cut padding, restated points, hedging, define-by-negation, mid-sentence em-dashes, and other AI writing tells, leaving substance, facts, and code unchanged. Use when writing or cleaning up any text a human will read (documents, READMEs, emails, posts, commit messages, PR descriptions), or whenever the user asks to "run write-better" or apply the Write Better style.
---

Run a Write Better style pass on the text in this conversation.

Enforce these core rules:

- **Say it once, precisely.** Cut any clause that restates an earlier one or argues a point no one would make.
- **No define-by-negation** ("X, not Y" where Y is a strawman). Keep the contrast only for an LLM reader ("read from the replica, not the primary" in an agent prompt or runbook) or a safety prohibition ("never force-push to main"); in human-facing prose, cut the foil even when Y was a real option.
- **No broad-to-narrow ramp** — one idea restated at escalating zoom. Lead with the precise version and stop.
- **Commas and semicolons over mid-sentence em dashes and colons.**
- **Future events in the future tense or a polite imperative, not the present** ("we will scope" / "please scope", not "Engineering scopes").
- **Plain verbs for plain actions** ("we'll defer pricing", not "pricing stays parked").
- **Complete the clause, including bold leads** — no bare fragments; a bold paragraph lead is a sentence and takes a verb ("The model gateway is a first-class component", not "Model gateway as a first-class component").

How to run the pass:

1. Fix the style violations above.
2. Keep guardrail negations for an LLM reader (agent prompts, runbooks, skills, tool descriptions) and safety prohibitions ("never force-push to main") for any audience. In human-facing prose, cut the foil and state the point positively.
3. Change nothing else: substance, facts, numbers, steps, structure, headings, and code stay untouched. This is a style pass, not a rewrite.
4. Report what you changed as a short list, so the edit is reviewable.

Expect the result to come out shorter.

The full rule catalog is in the repo's `style-guide.md` for anyone who wants the complete reference.
