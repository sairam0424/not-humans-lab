# docs/ — Not-Humans-Lab (system-level)

Diátaxis-based layout, scoped to cross-project content only. Each sub-project (once scaffolded) has its own `docs/` following the same four-way split for its own product-specific material — this one never duplicates that.

- **`docs/tutorials/`** — learning-oriented, cross-project onboarding (currently empty — no code exists yet to onboard to)
- **`docs/how-to/`** — task-oriented cross-project recipes (currently empty)
- **`docs/reference/`** — authoritative cross-project reference material (currently empty)
- **`docs/explanation/`** — background/rationale for why the suite is split the way it is, and the shared architecture — see `../architecture.md` for now; move detail here if it outgrows that file
- **`docs/adr/`** — numbered Architecture Decision Records, one immutable file per cross-project decision (see `0001-adopt-architecture-decision-records.md`)

## Root-level exceptions (stay at repo root, not under `docs/`)

`README.md`, `LICENSE`, `SECURITY.md`, `SUPPORT.md`, `AGENTS.md`, `CLAUDE.md`, `SOUL.md`, `Context.md`, `memory.md`, `architecture.md`, `tech.md`, `decisions.md`, `anti-patterns.md`, `agent_learning.md`, `logs.md`, `Branches.md`, `TESTING.md` — these stay at root because GitHub/npm/IDE tooling looks for several of them there by exact filename, and the rest follow this repo's own established Phase-0 convention.

No fifth category — if something doesn't fit tutorials/how-to/reference/explanation/adr, it probably belongs at repo root instead.
