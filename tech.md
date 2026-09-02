# tech.md — Not-Humans-Lab (system-level, intersection only)

This file lists **only** technology genuinely mandated across all three sub-projects. It is deliberately near-empty — an over-broad system `tech.md` would silently become a false mandate on projects that are free to choose independently.

## Stack summary table

| Layer | Choice | Status | Notes |
|---|---|---|---|
| License | Apache-2.0 | Adopt | Mandated identically across daily-dose, nh-deck, nh-skills — see `LICENSE` and `decisions.md`. |
| Branch/commit strategy | Trunk-based + Conventional Commits (see `Branches.md`) | Adopt | Mandated identically; drives automated semver/changelog per project. |
| Shared build/package-manager/CI runner | **None** | — | Explicitly not mandated. Each project independently chose: daily-dose → Astro + TS/Node; nh-deck → TS/Node + Commander.js; nh-skills → pure Markdown/YAML + one Node validator script. No monorepo tooling adopted at this level. |
| Shared runtime version floor | **None yet** | — | Not currently forced. Revisit only if a real shared dependency (e.g. a common validator library) emerges. |

## Rationale

Each of the three projects has a fully independent, already-researched tech stack fit to its own shape (a static content site + LLM pipeline; a CLI tool; a markdown collection). Forcing a shared runtime or build tool across three such different projects would add coordination cost with no demonstrated payoff — this mirrors the existing Not-Humans-World workspace convention of independent per-project toolchains with no root-level shared build/test/lint command.

## Version & upgrade policy

Not applicable at this level — no shared dependency to version. Each sub-project's own `tech.md` (once scaffolded) owns its version/upgrade policy.

## Constraints & non-negotiables

- Apache-2.0 license, non-negotiable across all three (enterprise-adoption rationale: explicit patent grant, unlike MIT).
- No project may silently diverge from the canonical `Branches.md` template without calling out the deviation inline in its own copy.

## Deprecated / Hold list

None yet.

## Local dev & tooling requirements

None at this level — this repo has no build, no dependencies, no local dev setup. Each sub-project's own `tech.md` covers its own requirements once scaffolded.
