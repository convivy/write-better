---
description: Run a Write Better style pass — tighten prose to the writing guide, change nothing else
argument-hint: "[file or path; omit to use the text just referenced]"
---

Run a **Write Better** style pass on $ARGUMENTS (if no argument was given, use the file or text I just referenced or selected).

Apply the Write Better writing guide. If the full guide is installed, follow it in full (for example `@~/.claude/rules/style-guide.md`, or your project's copy). Either way, enforce these core rules:

- **Say it once, precisely.** Cut any clause that restates an earlier one or argues a point no one would make.
- **No define-by-negation** ("X, not Y" where Y is a strawman). Keep the contrast only for an LLM reader ("read from the replica, not the primary" in an agent prompt or runbook) or a safety prohibition ("never force-push to main"); in human-facing prose, cut the foil even when Y was a real option.
- **No broad-to-narrow ramp** (one idea restated at escalating zoom).
- **Commas and semicolons over mid-sentence em dashes and colons.**
- **Future events in the future tense or a polite imperative, not the present** ("we will scope" / "please scope", not "Engineering scopes").
- **Plain verbs for plain actions** ("we'll defer pricing", not "pricing stays parked").
- **Complete the clause, including bold leads** (no bare fragments; a bold paragraph lead is a sentence and takes a verb: "The model gateway is a first-class component", not "Model gateway as a first-class component").

How to run the pass:

1. Fix the style violations above.
2. KEEP guardrail negations for an LLM reader (agent prompts, runbooks, skills, tool descriptions) and safety prohibitions ("never force-push to main") for any audience. In human-facing prose, cut the foil and state the point positively.
3. Change nothing else: substance, facts, numbers, steps, structure, headings, and code stay untouched. This is a style pass, not a rewrite.
4. Report what you changed as a short list, so the edit is reviewable.

Expect the result to come out shorter.
