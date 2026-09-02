# Context.md — Not-Humans-Lab

Living state-of-the-world doc. Agents should update this as work progresses — this is not a duplicate of AGENTS.md's static command list.

## What this is

The umbrella tying together three independent, now-shipped projects — daily-dose (AI-curated daily digest), nh-deck (local-first presentation CLI), nh-skills (AI-agent skills collection).

## Current state (as of 2026-09-02)

**All 7 phases of the original plan are complete.** All three sub-projects are live, standalone GitHub repos with green CI. See `status.md` for the full one-row-per-project rollup.

- **Naming: locked, partially registered.** Umbrella = Not-Humans-Lab (this repo itself is not yet its own GitHub repo/org — see Open questions). Sub-projects `daily-dose`, `nh-deck`, `nh-skills` are all registered and live under `github.com/sairam0424/`. The dedicated `not-humans-lab` GitHub org and `@not-humans-lab` npm scope are still **not** registered.
- **Tech stack: decided AND implemented, verified working:**
  - daily-dose → Astro (static) + TypeScript/Node pipeline; real live HN Algolia fetch, placeholder (non-LLM) scoring, real `astro build` producing a rendered page with real content
  - nh-deck → TypeScript/Node, Commander.js, marked, puppeteer-core + chrome-launcher, Vitest; `render` genuinely serves HTML over a real local HTTP server, `pdf` genuinely produced a real 57KB PDF via a detected local Chrome
  - nh-skills → pure Markdown + YAML frontmatter, one Node validator script; one real skill (`nh-commit`) shipped through a full author → validate → PR → CI → merge loop
  - system (this repo) → no runtime, no build — documentation and governance only, as decided
- **Documentation: complete at both levels.** System-level docs (this repo) plus each sub-project's own full pre-scaffold doc set, including `agent_learning.md`/`anti-patterns.md`/`status.md`/`Branches.md` files that were missing from the original Phase 0/1/3/5 passes and only caught during the Phase 7 audit (see `agent_learning.md` and `status.md`).
- **Not yet done, by explicit design, not oversight:** no real LLM API calls (no keys exist), no `schedule:` cron, no Vercel/hosting deployment, no arXiv sourcing for daily-dose, no npm publish for nh-deck/nh-skills, and no dedicated `not-humans-lab` GitHub org / npm scope (this repo itself is now live under the personal account, see below).

## Architecture at a glance

Three independent repos, no shared build graph. See `architecture.md` for the C4 Level-1 picture. The only cross-project relationship remains speculative (nh-skills eventually shipping a blog-to-deck-style skill that invokes nh-deck) — nothing has been built against that relationship yet, everything shipped so far is fully independent.

## Key decisions & why (short log — full detail in `decisions.md` / `docs/adr/`)

- **2026-09-02** — Chose Not-Humans-Lab over `@not-humans` for this umbrella once the internal collision (an unrelated pre-existing project of the same name) was resolved by renaming that project to "Not-Humans." Not-Humans-Lab had a clean external-availability verdict; `@not-humans` carried a soft collision with an unrelated fashion brand. See `docs/adr/0001-adopt-architecture-decision-records.md` for the ADR convention this and future decisions will follow.
- **2026-09-02** — License decided as Apache-2.0 across all three npm-published sub-projects (patent grant matters for enterprise adoption of a CLI/skills package; MIT was rejected for lacking one).

## Roadmap — 7-phase plan: complete

1. ~~Phase 0 — system docs~~ Done.
2. ~~Phase 1 — nh-skills pre-scaffold docs~~ Done.
3. ~~Phase 2 — nh-skills walking skeleton~~ Done — `nh-commit` merged via PR #1, CI green.
4. ~~Phase 3 — nh-deck pre-scaffold docs~~ Done.
5. ~~Phase 4 — nh-deck walking skeleton~~ Done — render+serve+PDF-export all verified working for real, CI green.
6. ~~Phase 5 — daily-dose pre-scaffold docs~~ Done.
7. ~~Phase 6 — daily-dose walking skeleton~~ Done — real HN fetch + placeholder scoring + real `astro build`, CI green.
8. ~~Phase 7 — cross-project reconciliation~~ Done — this pass. Found and fixed: missing `Branches.md` copies, missing `agent_learning.md`/`anti-patterns.md`/`status.md` files (a gap in the original per-phase scaffolding, not drift), a placeholder LICENSE copyright holder in this repo, and stale "(planned)"/"in progress" status language in nh-skills' own docs.

**Next priorities (post-plan, not yet started):** wire real LLM API keys into daily-dose's curation step; decide on Vercel deployment; consider the dedicated `not-humans-lab` GitHub org / `@not-humans-lab` npm scope registration now that all four repos in the suite are live and prove it's real.

## Open questions / known risks

- **This repo is now live**: github.com/sairam0424/not-humans-lab (created with fresh, explicit user confirmation, per its own `CLAUDE.md`'s requirement). It is under the personal account, not yet a dedicated `not-humans-lab` GitHub org.
- The dedicated `not-humans-lab` GitHub **org** (as opposed to this personal-account repo) and the `@not-humans-lab` npm scope remain **unregistered** — a third party could claim either before we do.
- The "system" tech-stack research input came back as a placeholder/error during the original research pass; the resulting decision (no shared runtime) is directionally sound but thinner-evidenced than the three project-level stack decisions.
- No real LLM API keys exist anywhere in the suite — daily-dose's curation is an honest placeholder, not a design limitation but a hard blocker on the roadmap's next real step.

---
*Last updated: 2026-09-02. Agents: keep this current as work progresses — do not let it go stale while AGENTS.md/SOUL.md/CLAUDE.md stay static.*
