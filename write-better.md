---
description: Run a Write Better style pass — tighten prose to the writing guide, change nothing else
argument-hint: "[file or path; omit to use the text just referenced]"
---

Run a **Write Better** style pass on $ARGUMENTS (if no argument was given, use the file or text I just referenced or selected).

Apply the Write Better writing guide. If the full guide is installed, follow it in full (for example `@~/.claude/rules/style-guide.md`, or your project's copy). Either way, enforce these core rules:

- **Say it once, precisely.** Cut any clause that restates an earlier one or argues a point no one would make.
- **No define-by-negation** ("X, not Y" where Y is a strawman) — but KEEP informative negations ("read from the replica, not the primary"; "do NOT …").
- **No broad-to-narrow ramp** (one idea restated at escalating zoom).
- **Commas and semicolons over mid-sentence em dashes and colons.**
- **Future events in the future tense or a polite imperative, not the present** ("we will scope" / "please scope", not "Engineering scopes").
- **Plain verbs for plain actions** ("we'll defer pricing", not "pricing stays parked").

How to run the pass:

1. Fix the style violations above.
2. KEEP guardrail negations and operational "do NOT" constraints — they carry information; stripping them removes a fence around a known failure.
3. Change nothing else: substance, facts, numbers, steps, structure, headings, and code stay untouched. This is a style pass, not a rewrite.
4. Report what you changed as a short list, so the edit is reviewable.

Expect the result to come out shorter.
