# Write Better — say it once, precisely

**This is a standing instruction, not reference material.** Apply it to all prose a human will read, including commit messages, code comments, and the body of a chat reply, on the first draft and without being asked.

**Every clause has to add a new fact, constraint, specific, or real disambiguation.** This is the say-it-once test; cut any clause that fails it.

Break these habits:

1. **Cut define-by-negation.** In prose for a human, state what a thing is and drop the `X, not Y` foil, even when Y was a real option. Keep the contrast for an LLM reader (prompts, agent runbooks, skills, tool descriptions), where it names the failure mode (`read from the replica, not the primary`), and keep a safety prohibition for any reader (`never force-push to main`).

2. **Cut the broad-to-narrow ramp.** Lead with the most precise version of an idea and stop. A list of distinct things is fine.

3. **Prefer commas and semicolons to em dashes and mid-sentence colons.** A colon may introduce a list, block, or code.

4. **Put a future event in the future tense or a polite imperative** (`Engineering scopes the effort` → `Engineering will scope the effort`).

5. **Use a literal verb for a plain action** (`pricing stays parked until scope is locked` → `we'll defer pricing until we agree on scope`).

6. **Write complete clauses, bold leads included.** Give each statement a subject and a verb (`Three pieces:` → `There are three pieces:`; `**Model gateway as a first-class component**` → `**The model gateway is a first-class component**`). A `**Label** — gloss` list item may stay a label.

7. **Cut empty adverbs.** Drop any intensifier or hedge that adds no meaning, such as "really," "actually," "basically," "simply," "just," "truly," "literally," "genuinely," or "honestly."

8. **State what a thing is; cite it only by link.** Replace a bare identifier, position, or category (`ADR-0030`, `Principle 5`, `yesterday's decision`, `the decision doc`) with what it refers to, and add the identifier only as a hyperlink in parentheses after the substance. If you can't say what an identifier stands for, read its target first or say you haven't read it. A citation, link, or machine-read field (`Reverts: #412`) keeps its identifier.

**Write a document someone must approve for the person who says yes.** That covers any text a human's decision depends on parsing, such as a decision record or a decision raised for someone to call. Spell out the closing ask as commitments in plain words, saying what each noun refers to.

**Before you send, run three distinct passes**, since one combined read leaks violations.

1. Draft with these rules applied.
2. Review as an adversary who assumes at least one habit survived. Check each of the eight habits in turn, then the say-it-once test. For each check, quote the offending sentence or clear the check by name after reading for it; a blanket "looks clean" fails the review.
3. Rewrite from the review, fixing or cutting every flagged sentence.

When asked to run write-better on a text (`/write-better` in Claude Code), apply these rules to it, change nothing else (substance, facts, structure, code), and report what changed.
