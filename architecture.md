# architecture.md — Not-Humans-Lab (System Context, C4 Level 1 only)

This file stops at C4 Level 1 deliberately. Each sub-project's own `architecture.md` (once scaffolded) picks up from C4 Level 2/3/4 for its own internals, treating the other two projects as external systems at its boundary.

## Introduction & Goals

Document how the three sub-projects relate to each other — nothing else. Top goal: keep each project genuinely independent (own repo, own toolchain, own release cadence) while making the few real relationships between them explicit and intentional rather than accidental.

## Constraints

- No shared build graph, shared dependency tree, or shared CI pipeline across the three projects (matches this workspace's existing convention for independent top-level projects).
- No monorepo tooling (Turborepo/pnpm workspaces) adopted at this level — deliberately, per the tech-stack research: each project's toolchain is small enough on its own that shared build tooling would add coordination cost without a proven need.

## Context & Scope — C4 Level 1 (System Context)

```
                    ┌─────────────────────────┐
                    │      Not-Humans-Lab      │
                    │   (docs + governance      │
                    │    only — no runtime)     │
                    └────────────┬─────────────┘
                                 │ (documentation, decisions,
                                 │  branch/license/testing templates)
        ┌────────────────────────┼────────────────────────┐
        │                        │                        │
┌───────▼────────┐      ┌────────▼────────┐      ┌────────▼────────┐
│   daily-dose     │      │     nh-deck      │      │    nh-skills     │
│  (AI-curated      │      │ (local-first      │      │ (AI-agent skills │
│  daily digest)    │      │  presentation CLI)│      │   collection)    │
└───────────────────┘      └────────▲────────┘      └────────┬────────┘
                                     │                        │
                                     └───── invokes (future) ──┘
                            nh-skills' blog-to-deck-style skill
                              is expected to call nh-deck
```

Three boxes, one identified arrow. Everything else is independent.

## Solution Strategy

Keep the umbrella as a documentation-and-governance layer only. Do not introduce shared infrastructure, shared auth, or a shared design-token package until a concrete need forces the question (YAGNI) — see `decisions.md` for how that promotion would be recorded if it ever happens.

## Building Block View

Stops at "each project = one box" (above). No further decomposition belongs in this file — see each sub-project's own `architecture.md` once it exists.

## Runtime View

No cross-project runtime flow exists yet beyond the single identified relationship above (nh-skills → nh-deck, not yet implemented).

## Deployment View

Covers only shared/umbrella infrastructure — currently none. Each project deploys independently (daily-dose to a static host with a scheduled pipeline; nh-deck and nh-skills publish to npm; see each project's own `deploy.md` once scaffolded).

## Crosscutting Concepts

- **License**: Apache-2.0, decided once here, applied identically to all three (see `LICENSE`).
- **Branch/release strategy**: one canonical template (see `Branches.md`), copied verbatim into each repo.
- **Naming**: Not-Humans-Lab (org/scope) + daily-dose/nh-deck/nh-skills (projects) — see `decisions.md`.

## Architecture Decisions

See `docs/adr/` — currently one entry (`0001-adopt-architecture-decision-records.md`). Each sub-project keeps its own independent ADR sequence starting at 0001; this repo's sequence is reserved for decisions that constrain or cut across two or more sub-projects.

## Quality Requirements

Cross-project only: consistent branch/license/testing conventions (enforced via the templates in this repo), consistent doc structure (`docs/README.md`) so an agent or contributor never has to guess where something lives.

## Risks & Technical Debt

- No sub-project exists yet, so this architecture is unvalidated against real code.
- The single identified cross-project relationship (nh-skills → nh-deck) is speculative until nh-skills actually ships that skill.

## Glossary

- **Umbrella / system level** — this repo; describes relationships between projects, never one project's internals.
- **Sub-project** — daily-dose, nh-deck, or nh-skills, each its own independent repo.
