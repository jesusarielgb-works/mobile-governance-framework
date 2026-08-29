# 00 — Governance & Agile

Governance wraps every other section. It defines how the team works, decides, and ships.

## Agile Cadence

| Ceremony | Frequency | Output |
|----------|-----------|--------|
| Sprint planning | Per sprint (1–2 weeks) | Committed backlog for the sprint |
| Daily standup | Daily, ≤ 15 min | Blockers surfaced |
| Backlog refinement | Weekly | Stories estimated and ready |
| Sprint review | End of sprint | Demo on a real device/build |
| Retrospective | End of sprint | Action items with owners |

## Definition of Ready (DoR)

A story enters a sprint only when:
- User value and acceptance criteria are written.
- UI reference (design/mockup) is linked when the story touches UI.
- API contract is available or stubbed.
- Estimated by the team.

## Definition of Done (DoD)

A story is done only when:
- Code merged to the main branch via reviewed PR.
- Tests added and passing (see [04 - Quality & Testing](04-quality-and-testing.md)).
- Runs on both target platforms without regressions.
- No new linter or accessibility warnings introduced.

## Branching

- Trunk-based with short-lived branches off `main`.
- Branch names: `feat/<scope>`, `fix/<scope>`, `chore/<scope>`.
- Conventional Commits: `feat:`, `fix:`, `refactor:`, `test:`, `docs:`, `chore:`.
- One PR = one story or fix. Squash-merge.

## Versioning

- App version: [SemVer](https://semver.org/) `MAJOR.MINOR.PATCH`.
- Build number: monotonic integer, incremented every store upload.
- Tag releases `vX.Y.Z` — the tag triggers the release pipeline.

## Decisions

- Record significant technical decisions as short ADRs (context → decision → consequences).
- Governance rules here are defaults; a team may override a rule with a documented ADR.
