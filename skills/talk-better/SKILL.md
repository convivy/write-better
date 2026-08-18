---
name: talk-better
description: Strip conversational AI tells from a reply or chat transcript — validation openers ("Great question"), eager preamble, generic sign-offs, performed sincerity ("honestly," "genuinely"), stock framing ("the move here"), reflexive emoji, therapy-speak, and decision-dodging hedges — keeping the substance and the genuine gated exceptions. Use when cleaning up a draft chat reply or a pasted conversation, or whenever the user asks to "run talk-better."
---

Run a talk-better pass on the draft reply or transcript in this conversation.

Enforce these core rules for each turn:

- **No validation opener.** Cut "Great question!", "You're absolutely right!", and similar openers. The answer opens on substance.
- **No performed willingness.** Cut preamble ("Certainly! I'd be happy to…") and generic sign-offs ("Let me know if you need anything!"). Keep a specific next-step offer that names a concrete action.
- **No sycophantic reversal.** Where a turn caves under pushback with no new argument, flag it. Keep concessions of real errors, with the reason stated.
- **No default affect mismatch.** Strip emoji and exclamation-point enthusiasm where the content carries none; keep it where the turn's register genuinely calls for it.
- **No performed sincerity.** Cut "honestly," "genuinely," "to be honest," "frankly" used as sincerity signals or empty intensifiers.
- **No stock framing.** Replace "X is the move here" and similar phrases with the actual statement and reason. Citing an identifier as the reason ("per ADR-0030," "that's what Principle 5 says") is the same substitution.
- **No therapy-speak on ordinary requests.** Cut reflexive emotional validation on a turn that only needs a fix. Keep proportionate acknowledgment of real distress.
- **No decision-dodging hedges.** Where the user asked for a call and got stacked hedges, flag it and prefer a stated recommendation with the reason.
- **No question read-back when nothing was ambiguous.** Cut turns that replay the question before answering it. Keep a one-line restatement that resolves a genuine fork.
- **No over-structuring a small answer.** Remove headers and bullet scaffolding from answers that read cleanly as prose. Keep structure where the content is genuinely a list, sequence, or comparison.

Run the pass in three stages. Keep them distinct; a single combined read is what lets tics through.

1. **Fix** each tic above wherever it appears in the draft or transcript.
2. **Review as an adversary.** Re-read the fixed text as a critic who assumes at least one tic survived and means to catch it. Go tic by tic through the list above. For each tic, quote a still-violating line, or clear that tic by name. A blanket "looks clean" is a failed review; you clear a tic only after reading for it.
3. **Rewrite** from the review, fixing or cutting every line it flagged.

Across all three stages:

- **Keep the gated exceptions:** a specific next-step offer naming a concrete action, a concession of a real error with the reason, and proportionate acknowledgment of real distress.
- **Change nothing else:** the substance, facts, numbers, steps, and code stay untouched. This is a conversational-frame pass, not a content rewrite.
- **Report what changed** as a short list, naming the tic each edit served, so the pass is reviewable.

Expect the result to come out shorter.

The full ten-tic catalog, with mechanisms, before/after pairs, and extended exceptions, is in the repo's `talk-better-guide.md`.
