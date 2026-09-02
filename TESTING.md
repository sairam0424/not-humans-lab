# TESTING.md — Not-Humans-Lab (canonical template)

This is the shared skeleton every sub-project fills in with its own ratios and script list, so a human or agent jumping between repos always finds the same headings. Do not invent new section names in a project-level copy — fill these in instead.

## Test Philosophy

State here (per project) whether this project uses a pyramid (many unit, fewer integration, few e2e — right for deterministic logic) or a trophy shape (mostly integration, thin unit layer — right when static typing/schemas already catch most shape bugs), and why.

## Test Pyramid / Trophy by Layer

Table: layer name → target ratio → what it's allowed to touch (mocks vs. real network vs. real filesystem).

## Project-Specific Test Forms

Whatever this project's category needs beyond unit/integration/e2e — decided per project:

- **daily-dose**: content-schema validation tests, LLM-output golden-file/snapshot tests (deterministic via recorded fixtures, never live API calls in the blocking gate), a separate non-blocking `test:eval` for output-quality scoring.
- **nh-deck**: CLI-output snapshot tests (stdout/stderr/exit-code, non-deterministic fields normalized), an `npm pack` + install-into-temp-dir smoke test before publish.
- **nh-skills**: SKILL.md frontmatter schema/structural lint (this project's "static" base layer), trigger-accuracy integration tests, a non-blocking end-to-end eval layer run weekly/pre-release rather than per-commit.

## Required npm Scripts

Kept name-identical across all three repos: `test` (the full blocking gate), `test:unit`, `test:integration`, `test:e2e`, `test:watch`, `test:coverage` (enforces this workspace's 80% floor), plus one project-specific script per category (`test:schema` + `test:eval` for daily-dose; `test:snapshot` for nh-deck; `test:lint-skills` + `test:trigger` for nh-skills).

## Coverage Thresholds

80% floor (workspace-wide global rule), numerically enforced via `test:coverage`. State per project what's excluded and why (e.g. generated files, vendored templates).

## Fixtures & Golden Files

Location convention + how golden files get reviewed/updated deliberately — as a reviewed diff, never auto-accepted.

## Non-Determinism Policy

How LLM-output or timing-dependent tests are made deterministic (recorded fixtures, pinned temperature) or explicitly quarantined from the blocking gate (a separate, non-blocking eval script).

## Test File Naming & Location

Mirrors `src/` per the global coding-style convention: `*.test.ts` colocated, or under `tests/` — decided per project, stated explicitly in that project's own copy of this file.

---

*This file is the template. Each of daily-dose/nh-deck/nh-skills copies it in once scaffolded and fills in its own ratios/scripts — do not leave any project's copy as an unfilled template past its own Phase 2/4/6 walking-skeleton milestone.*
