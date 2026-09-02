# decisions.md — Not-Humans-Lab (index + lightweight log)

**Scope of "architecturally significant" at this level:** a decision that constrains or cuts across two or more of daily-dose/nh-deck/nh-skills. Anything scoped to a single project belongs in that project's own `decisions.md`, not here.

## ADR Index

| ID | Title | Status | Date |
|---|---|---|---|
| [0001](docs/adr/0001-adopt-architecture-decision-records.md) | Adopt Architecture Decision Records | Accepted | 2026-09-02 |

## Lightweight Decisions Log

| Date | Decision | Rationale | Owner |
|---|---|---|---|
| 2026-09-02 | Umbrella name = Not-Humans-Lab (not `@not-humans`) | Internal collision with a pre-existing unrelated project resolved by renaming that project to "Not-Humans"; Not-Humans-Lab's external availability was cleanest of all candidates researched | user |
| 2026-09-02 | License = Apache-2.0 for all three sub-projects | Explicit patent grant matters more for enterprise adoption than MIT's silence on patents; consistency across all three signals a deliberate choice to reviewers | user |
| 2026-09-02 | No monorepo tooling / no shared build graph at the system level | Each sub-project's independent tech stack is small enough on its own; matches the existing Not-Humans-World workspace convention | user |

## Cross-links

None yet — no sub-project `decisions.md` exists to link to. Add a row here once each of daily-dose/nh-deck/nh-skills has its own.
