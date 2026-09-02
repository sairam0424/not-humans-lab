# agent_learning.md — Not-Humans-Lab (system-level)

Append-only, dated register of corrections applied to AI agents working across the suite — companion to `AGENTS.md`/`CLAUDE.md` (which hold current-state static instructions), not a replacement. This file holds the *history of why* those instructions exist.

**Scope:** cross-project agent-behavior learnings only (shared conventions, cross-project coordination mistakes, shared-tooling gotchas). Learnings specific to one sub-project's own code/domain belong in that project's own `agent_learning.md`.

**Promotion path (two-stage):**
1. A learning that recurs in two or more sub-project `agent_learning.md` files gets copied up here.
2. Once a learning here (or a repeatedly-confirmed project-level one) stabilizes, it gets promoted **out** of this log entirely and folded into the relevant `AGENTS.md`/`CLAUDE.md` as a standing instruction, with its entry here marked `Status: promoted-to-AGENTS.md` and linked.

## Entries

### 2026-09-02 — Parallel docs-writing agents describe aspirational structure that drifts from what code-writing agents actually build

- **Trigger**: caught independently in all three sub-projects during their own Phase 1-6 builds, without ever being logged as a shared pattern until this Phase 7 reconciliation pass.
- **Observation**: when documentation (AGENTS.md, Context.md, codebase_map.md) and skeleton code were written by separate parallel agents from the same task spec, the docs agents repeatedly described a directory/file layout that never matched what the code agent actually implemented — not a typo, a genuinely different imagined structure. Concretely: nh-deck's docs described `src/commands/`, `src/render/`, `src/server/`, `src/export/` subdirectories and a `test/__snapshots__/` convention; the real code was flat (`src/render.ts`, `src/server.ts`, `src/pdfExport.ts`) with no Vitest snapshot files at all. daily-dose's docs described a single array-per-day digest file and a separate `src/components/ScoreChart.astro`; the real, working code (after a separate schema-compatibility fix) writes one file per story and renders the chart inline in `index.astro`. nh-skills' own `AGENTS.md` pointed at `scripts/validate-skills.test.mjs` for its test file when the real path was `test/validate-skills.test.mjs`.
- **Root cause**: giving a docs-writing agent and a code-writing agent the same conceptual spec (in prose) rather than the same concrete artifact does not guarantee they converge on identical file paths — each independently "fills in" plausible-sounding structural details the prompt didn't pin down byte-for-byte, and neither agent sees the other's actual output before finishing.
- **Correction / Rule**: after any workflow that runs docs-writing and skeleton-writing agents in parallel from a shared spec, run a final grep sweep across the new docs for concrete file/directory/function names and diff each one against the real file tree before shipping — do not trust a docs agent's own self-report that its content is accurate. This is now standing practice, not optional cleanup.
- **Scope**: system-wide — recurred independently in all three sub-projects (nh-skills, nh-deck, daily-dose), so it is a property of the parallel-docs-plus-code workflow pattern itself, not any one project's carelessness.
- **Status**: active. One-line pointers left in each sub-project's own `agent_learning.md`.

### 2026-09-02 — ConfigProtection blocks tsconfig.json creation in any new project with its own package.json

- **Trigger**: hit for real during nh-deck's Phase 4 skeleton build; anticipated and pre-empted for daily-dose's Phase 6 build by proactively adding its path to the allowlist before running that workflow.
- **Observation**: the machine-global `~/.claude/hooks/config-protection.js` PreToolUse hook blocks any Write/Edit/Bash write to a file named `tsconfig.json` (or several other lint/format configs) whenever the target directory has a real project-root marker (a `package.json`, among others) anywhere in its ancestry — which includes the new project's own just-written `package.json`, not only some unrelated stray file. A subagent hit this mid-workflow for nh-deck and correctly stopped rather than routing around it; the user then explicitly approved a scoped, exact-path exception (`ALLOW_CONFIG_PATHS`) mirroring the existing `DestructiveGuard` `ALLOW_PUSH_ROOTS` pattern.
- **Root cause**: any brand-new TypeScript/Node sub-project scaffolded with its own `package.json` will trip this exact same block on its first `tsconfig.json`, every time — it is not a one-off, it is structural to how the hook defines "a real project."
- **Correction / Rule**: once the user has approved this scoped-allowlist pattern for one project, proactively add a new sub-project's anticipated `tsconfig.json` path to `ALLOW_CONFIG_PATHS` *before* running a scaffold workflow that will create one, rather than waiting for the block and round-tripping mid-workflow. Still add paths one at a time, by exact absolute path, never a directory-wide or blanket exception — the hook's protection must stay intact for everything else.
- **Scope**: system-wide — applies to any future TypeScript/Node sub-project in this suite (or this workspace) with its own `package.json`.
- **Status**: active. One-line pointers left in nh-deck's and daily-dose's own `agent_learning.md` (nh-skills is plain JavaScript with no `tsconfig.json`, so it never hit this).

## Entry format

- **Date**
- **Trigger** — what prompted the entry
- **Observation** — what the agent did or assumed, verbatim where useful
- **Root cause** — why the agent got it wrong
- **Correction / Rule** — the concrete, checkable rule now in force
- **Scope** — this-project-only vs. system-wide
- **Status** — active | superseded | promoted-to-AGENTS.md (with a link to where it landed)
