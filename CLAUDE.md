@AGENTS.md

## Claude Code

This addendum is pure navigation — Claude-specific behavior on top of the shared instructions in `AGENTS.md`.

- **This repo has no code.** Do not run build/test/lint tools here, do not scaffold a `package.json`, and do not `git init` this directory without the user explicitly asking — as of Phase 0 this is intentionally docs-only.
- **Routing rule:** if the user's request is about daily-dose, nh-deck, or nh-skills specifically, `cd` into that project's own (future) repo and load its own `CLAUDE.md`/`AGENTS.md` instead of acting from here.
- **Plan-mode trigger:** before writing any code that scaffolds one of the three sub-projects for the first time, confirm the phase sequencing in `Context.md` (nh-skills → nh-deck → daily-dose, docs-before-code within each) rather than jumping ahead.
- **Naming is not yet registered.** Treat "Not-Humans-Lab" (GitHub org, `@not-humans-lab` npm scope) as a decided-but-unregistered name. Do not run `gh repo create`, `npm publish`, or register any domain on the user's behalf without an explicit, fresh confirmation — this mirrors the same caution already applied when this name was chosen.
- **Size budget:** this file should stay well under 200 lines. If Claude-specific guidance grows, push detail into `.claude/rules/*.md` at this level rather than inlining it here.

No divergence from `AGENTS.md` is currently in force.
