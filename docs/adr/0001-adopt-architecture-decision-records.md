# 0001. Adopt Architecture Decision Records

## Status

Accepted — 2026-09-02

## Deciders

user

## Context and Problem Statement

The Not-Humans-Lab umbrella and its three sub-projects (daily-dose, nh-deck, nh-skills) will accumulate architecturally-significant decisions over time (naming, licensing, shared conventions, and eventually real cross-project contracts). Without a durable record, future contributors — human or agent — will have to reverse-engineer *why* a choice was made from git history alone, which is lossy and slow.

## Decision Drivers

- Need an immutable, dated record of significant decisions and their consequences (including negative ones).
- Need independent numbering per scope (this repo vs. each of the three sub-projects) so concurrent decisions across repos never collide.
- Should be lightweight enough that a solo maintainer actually keeps using it.

## Considered Options

1. No formal record — rely on commit messages and PR descriptions.
2. A single running `decisions.md` with no per-decision files.
3. Michael Nygard's ADR format (one immutable file per decision, sequential numbering, `docs/adr/`).

## Decision Outcome

We will adopt option 3: Michael Nygard's ADR format, one file per decision under `docs/adr/`, numbered sequentially and zero-padded (`NNNN-title-with-dashes.md`), never renumbered or edited after acceptance — only superseded by a new, later-numbered ADR. This repo (Not-Humans-Lab) keeps its own independent sequence starting here at 0001, reserved for decisions spanning two or more sub-projects. Each sub-project will keep its own independent 0001-up sequence once scaffolded.

## Consequences

**Good, because:**
- Every future significant decision has a permanent, searchable record with its actual reasoning, not just its outcome.
- Superseding a decision is explicit (a new ADR, with the old one's status flipped) rather than a silent edit that erases history.

**Bad, because:**
- Adds a small amount of process overhead per significant decision (writing the ADR) that a purely commit-message-driven approach wouldn't have.
- Requires discipline to actually use it rather than letting decisions live only in chat/PR discussion.

## Confirmation

Any future decisions.md entry that graduates from the lightweight log to "architecturally significant" should get its own numbered file here (or in the relevant sub-project's own `docs/adr/`), following this same format.

## More Information

`decisions.md` in this repo indexes this ADR and any future ones. `docs/README.md` explains where `docs/adr/` sits within the overall docs/ layout.
