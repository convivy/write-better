# Write Better

Write Better is a small, drop-in style guide that makes Claude write plainly and specifically, and stops the padded, hedged, restated prose AI tends to produce. It's for anyone who writes with Claude, and it's free to use, change, and pass on.

There are three pieces:

- **`essentials.md`** — a short block (~400 words) of always-on rules. Paste it into wherever your Claude reads standing instructions.
- **`style-guide.md`** — the full rule catalog. Keep it as a reference document Claude can consult when you're writing or editing something that matters.
- **`write-better.md`** — a `/write-better` slash command for Claude Code that runs the pass on a document on demand.

The essentials work on their own. The full guide and the command are there for thorough, on-demand edits.

---

## Install it

### Claude Code (the CLI)

- **Essentials** → paste into `~/.claude/CLAUDE.md` (applies everywhere) or a project's `CLAUDE.md` (that project only). Keep this file short; it loads into every session.
- **Full guide** → drop `style-guide.md` into `~/.claude/rules/` (or anywhere in your repo). To pull it in automatically, add one line to your `CLAUDE.md`: `@~/.claude/rules/style-guide.md`. Otherwise just tell Claude to read it when you need a thorough pass.
- **Command** → drop `write-better.md` into `~/.claude/commands/` (applies everywhere) or a project's `.claude/commands/`. Then type `/write-better` (optionally with a file or path) to run a style pass on demand.

### Claude.ai (the web app)

- **Essentials** → Settings → Profile → the "personal preferences" / instructions field. It applies to every conversation. (Aim for a few short paragraphs; this field shares your conversation's budget.)
- **Full guide** → on paid plans, create a Project and upload `style-guide.md` as a project file, so it's available in every chat in that project. On the free plan, paste it at the top of a conversation when you want a thorough edit.
- Note: unlike Claude Code, the full guide does not load on its own here, so add it to a Project or paste it in.

### Claude Cowork (in the Claude desktop app)

- **Essentials** → Settings → Cowork → Global Instructions. It's prepended to every Cowork task. (Cowork's instructions are separate from the web app's preferences, so set both if you use both.)
- **Full guide** → upload `style-guide.md` as a context file on the relevant Cowork project, and reference it by name from your global instructions.

---

## Using it

Once the essentials are in place, Claude follows them by default. Two things to know:

- **`/write-better`** in Claude Code, or **"run write-better on this"** in Claude.ai / Cowork, runs a focused edit on a document. It fixes the style, keeps the guardrail negations, changes nothing else, and reports what it changed. Expect the result to come out shorter.
- **Make it yours.** The catalog is a starting point. Add your own rules with the template at the bottom of `style-guide.md`.

---

*A free tool from Convivy.*
