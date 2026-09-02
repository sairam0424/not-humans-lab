# logs.md — Not-Humans-Lab (system-level rollup)

Internal day-to-day engineering/agent activity narrative — explicitly **not** the release-facing changelog (see `changelog/` for that, once any sub-project ships a release). This file is a cross-project rollup only; it is not a copy of any sub-project's own devlog.

| Date | Scope/area | What happened | Outcome/status | Links |
|---|---|---|---|---|
| 2026-09-02 | system | Deep-researched three reference repos (deckrun, ape-skills, the-daily-diff); ranked and chose to build daily-dose, nh-deck, nh-skills | Names locked | — |
| 2026-09-02 | system | Naming research surfaced internal collision: "Not-Humans-Lab" was already the name of a pre-existing, unrelated project in this workspace | Resolved | see decisions.md |
| 2026-09-02 | system | Renamed the pre-existing project to "Not-Humans" (GitHub repo `sairam0424/not-humans-lab` → `sairam0424/not-humans`, local dir renamed, all internal references patched, `package-lock.json` regenerated) | Done | Not-Humans-World/CLAUDE.md, Not-Humans/{package.json, CLAUDE.md, README.md, AGENTS_LEARNING.md, .github/workflows/auto-pr.yml} |
| 2026-09-02 | system | Freed "Not-Humans-Lab" for this umbrella; wrote Phase 0 system-level docs (this repo) | Done | this repo |

Each sub-project keeps its own `logs.md` for its own activity once scaffolded; only cross-project events, coordinated releases, or shared-infra changes get logged here.
