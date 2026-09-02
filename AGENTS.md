# AGENTS.md — Not-Humans-Lab (umbrella)

This file follows the vendor-neutral [AGENTS.md](https://agents.md) open specification. It is the routing layer only — Not-Humans-Lab itself has no shared build/test/lint graph.

## What this repo is

Not-Humans-Lab is a thin umbrella tying together three independent, separately-repo'd projects:

- **daily-dose** — a daily AI-curated arXiv + Hacker News digest
- **nh-deck** — a local-first Markdown/HTML presentation CLI
- **nh-skills** — a personal collection of AI-agent Skills

Each is its own git repository with its own toolchain, its own `AGENTS.md`, and its own build/test/lint commands. **There is no shared build, no shared dependency tree, and no shared CI pipeline across the three.** This repo holds only cross-cutting documentation and governance — never assume a command or convention from one sub-project applies to another.

## Setup / Environment

Nothing to install at this level. This is a documentation-only repo (no `package.json`, no build tooling). Once the three sub-project repos exist, install/build/test inside each one individually per its own `AGENTS.md`.

## Build, Run & Test Commands

None at this level. Do not run build/test commands from this directory.

## Routing — read this before doing anything

1. Determine which of daily-dose / nh-deck / nh-skills the task actually belongs to.
2. `cd` into that project's own repository.
3. Read **that** project's own `AGENTS.md` and follow it. It is the source of truth for that project's commands, conventions, and constraints — this file is not.

If the task is genuinely cross-project (affects two or more of the three), read this repo's `architecture.md` and `decisions.md` first, and write a `docs/adr/` entry here rather than in any single sub-project.

## Code Style & Conventions

Defined per sub-project. This repo has no source code of its own to style.

## Directory / Architecture Map

See `architecture.md` (C4 Level-1 system context — the three projects as boxes) and `docs/README.md` (the docs/ folder layout convention shared across all four repos in this suite once they exist).

## Commit & PR Conventions

See `Branches.md` — the canonical branch/commit/PR strategy, copied verbatim into each of the three sub-project repos once scaffolded. Applies identically at this umbrella level for any cross-cutting doc changes.

## Security & Safety Notes

See `SECURITY.md`. Never register a real npm scope, GitHub org, or domain on behalf of a user without explicit confirmation — naming decisions in this repo are recommendations, not executed registrations, until the user says otherwise.

## Known Gotchas / Anti-Patterns

See `anti-patterns.md` — currently empty (no sub-project code exists yet). Entries land here only once they recur in two or more of the three projects; single-project anti-patterns belong in that project's own file.

## Nested AGENTS.md

Once daily-dose/, nh-deck/, and nh-skills/ exist as sibling repos with their own `AGENTS.md`, an agent working inside one of them should read the **nearest** AGENTS.md in the tree (that project's own file), not this one — this file's job is routing, not per-project instruction.
