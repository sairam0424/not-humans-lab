# status.md — Not-Humans-Lab (system-level rollup)

A living, one-row-per-project snapshot — the durable answer to "what's shipped, what's in flight, what's blocked" without opening all three repos. Each row links to that project's own full-detail `status.md`, never duplicates it.

*Last updated: 2026-09-02.*

## Rollup

| Project | Health | Current state | Blockers | Own status.md |
|---|---|---|---|---|
| **nh-skills** | 🟢 Stable | Phase 1+2 complete. One real skill (`nh-commit`) merged via PR #1 through the full author → validate → PR → CI → merge loop. `npm run validate` and `npm test` both green. | None active. Next skill addition is the real test of repeatability. | `../nh-skills/status.md` |
| **nh-deck** | 🟢 Stable | Phase 3+4 complete. `render` genuinely serves HTML over a real local server; `pdf` genuinely produced a real PDF via a detected local Chrome. `npm run build` and `npm test` both green, CI green. | No 3-OS CI matrix yet (single ubuntu-latest job by design). No `npm publish` wired up. | `../nh-deck/status.md` |
| **daily-dose** | 🟡 Active, blocked on keys | Phase 5+6 complete. Real live HN Algolia fetch, placeholder (non-LLM) scoring, `astro build` renders real content. `npm run build` and `npm test` both green, CI green. | **No LLM API keys exist** — real curation cannot start until keys are provided. No cron, no Vercel deployment (both require explicit user go-ahead). | `../daily-dose/status.md` |
| **Not-Humans-Lab (this repo)** | 🟢 Live, docs-only | Phase 0 + Phase 7 complete. Live at github.com/sairam0424/not-humans-lab. All cross-cutting docs in place, `agent_learning.md` holds 2 real cross-cutting learnings, `Branches.md`/`LICENSE` reconciled against all three sub-projects. | No dedicated `not-humans-lab` GitHub **org** (this is a personal-account repo) / `@not-humans-lab` npm scope yet — not blocking, just not decided. | (this file) |

## Recent progress (this session)

- All three sub-projects scaffolded, built, tested, and shipped with green CI (Phases 1-6).
- Phase 7 reconciliation caught and fixed: missing `Branches.md` copies in all three sub-projects (relative-path-only references break for a standalone clone), missing `agent_learning.md`/`anti-patterns.md` in all three sub-projects, a missing `status.md` at the system level (this file), a placeholder LICENSE copyright holder in this repo, and stale "(planned)"/"in progress" language in nh-skills' `Context.md`/`codebase_map.md` that hadn't been refreshed after `nh-commit` actually merged.
- Two genuinely recurring cross-project learnings logged in `agent_learning.md`: aspirational-docs-vs-real-code drift (observed in all three projects independently), and ConfigProtection blocking `tsconfig.json` creation in any new TS/Node sub-project (observed in nh-deck and daily-dose).

## Upcoming milestones

1. Provide real LLM API keys to unblock daily-dose's actual curation step.
2. Decide on Vercel deployment and the `schedule:` cron for daily-dose.
3. Grow nh-skills' catalog past one skill; revisit tooling only at ~30-40 skills or outside contributors.
4. Consider `npm publish` for nh-deck and nh-skills once each has had more real-world use.
5. Consider a dedicated `not-humans-lab` GitHub org and `@not-humans-lab` npm scope now that all four repos are live under the personal account.

## Risks & blockers (cross-project)

- No LLM API keys anywhere in the suite — the single biggest blocker on daily-dose's roadmap, and on nh-skills eventually shipping any skill-authoring assistance that itself needs a model call.
