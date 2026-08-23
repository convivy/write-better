# Write Better

Write Better is a small, drop-in style guide that makes Claude write plainly and specifically, and stops the padded, hedged, restated prose AI tends to produce. It's for anyone who writes with Claude, and it's free to use, change, and pass on.

There are three pieces:

- **`essentials.md`** — a short block (~1,050 words) of always-on rules. Paste it into wherever your Claude reads standing instructions; once it's in, Claude writes in this style by default, with no command to invoke.
- **`style-guide.md`** — the full rule catalog. Keep it as a reference document Claude can consult when you're writing or editing something that matters.
- **`write-better.md`** — a `/write-better` slash command for Claude Code that runs the pass on a document on demand.

The essentials work on their own. The full guide and the command are there for thorough, on-demand edits.

---

## talk-better

talk-better is a companion guide for the conversational frame of a live chat turn: the openers, preambles, sign-offs, validation moves, and affect choices that surround an answer. Write Better governs composed prose; talk-better governs the frame. In a single reply, both apply.

There are three pieces:

- **`talk-better-essentials.md`** — the always-on block for live turns. It covers the seven most common conversational tells and installs the same way as `essentials.md`.
- **`talk-better-guide.md`** — the full eleven-tic catalog, with the mechanism for each tell, before/after pairs, and gated exceptions. Pull it on demand the same way as `style-guide.md`.
- **`talk-better.md`** — the `/talk-better` slash command, a cleanup pass for a draft reply or pasted transcript, parallel to `/write-better`.

---

## Install it

### Claude Code (the CLI)

- **Essentials** → paste into `~/.claude/CLAUDE.md` (applies everywhere) or a project's `CLAUDE.md` (that project only). Keep this file short; it loads into every session. Paste `talk-better-essentials.md` into the same file, after the Write Better block.
- **Full guide** → drop `style-guide.md` into `~/.claude/rules/` (or anywhere in your repo). To pull it in automatically, add one line to your `CLAUDE.md`: `@~/.claude/rules/style-guide.md`. Otherwise tell Claude to read it when you need a thorough pass. Install `talk-better-guide.md` the same way, as `@~/.claude/rules/talk-better-guide.md`.
- **Commands** → drop `write-better.md` and `talk-better.md` into `~/.claude/commands/` (applies everywhere) or a project's `.claude/commands/`. Then type `/write-better` or `/talk-better` (optionally with a file or draft) to run either pass on demand.

### Claude.ai (the web app)

These instructions reflect the current Claude.ai UI; label names may shift between releases.

- **Essentials (always-on)** → Settings → General → the "Instructions for Claude" box. Paste the Write Better essentials there, then paste `talk-better-essentials.md` below it. The field applies to every conversation and shares the conversation's context budget, so keep it to a few short paragraphs.
- **On-demand passes** → install the skills: download the `skills/write-better` and `skills/talk-better` folders from this repo, zip each folder, and upload each under Settings → Skills (also reachable as Customize → Skills). Once installed, each skill auto-triggers from its description, or you can say "run write-better on this" / "run talk-better on this." There is no slash-command syntax on the web.
- **Full guides (optional, paid plans)** → you can keep `style-guide.md` and `talk-better-guide.md` as project files in a Claude.ai Project for always-available reference; on the free plan, paste either guide into a conversation when you want a thorough edit.

### Claude Cowork (in the Claude desktop app)

- **Essentials** → Settings → Cowork → Global Instructions. It's prepended to every Cowork task. (Cowork's instructions are separate from the web app's preferences, so set both if you use both.) Paste `talk-better-essentials.md` into the same field.
- **Full guides** → upload `style-guide.md` and `talk-better-guide.md` as context files on the relevant Cowork project, and reference them by name from your global instructions.

---

## Using it

Once the essentials are in place, both guides are on by default. Claude applies Write Better to everything it writes for a human reader (documents, READMEs, commit messages, chat replies) and applies talk-better to the conversational frame of every live turn, automatically, the first time, without you invoking anything.

`/write-better` is for cleaning up text that wasn't written under the standard: a hand-written draft, pasted text, or an older document. It fixes the prose style, keeps the guardrail negations, changes nothing else, and reports what it changed. `/talk-better` does the parallel job on a draft reply or pasted transcript: it strips the conversational tells, keeps the gated exceptions, changes nothing else, and reports what it changed. Run either in Claude Code, or say "run write-better on this" / "run talk-better on this" in Claude.ai or Cowork. Expect the result to come out shorter.

**The catalogs are starting points.** Add your own prose rules with the template at the bottom of `style-guide.md`, and your own conversational rules with the template at the bottom of `talk-better-guide.md`.

---

*A free tool from Convivy.*
