# Changelog
Format: [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) | [SemVer](https://semver.org/)
## [Unreleased]
## [1.1.0] - YYYY-MM-DD
### Added
- Evidence from the engineering casebook on five rules: contrast [BIB-003], cold-start
  budget [BIB-004], feature flags [CASE-001], staged rollout [CASE-002], dependency
  scanning [CASE-004]
- `docs-check` workflow: links, citations and territory checked on every pull request
- `CITATION.cff`
### Changed
- The cold-start budget now says it is a project budget, stricter than the platform's threshold
- Feature flags: a retired flag is never reused for new behavior
## [1.0.0] - 2026-08-28
### Added
- Manual-style governance scaffold for mobile apps: numbered sections, each with a README and copy-and-fill templates
- `00-sdd-guide.md` — methodology and fill-in order
- 00-governance: agile, git, DoR/DoD, security rules + sprint-retro template
- 01-architecture: structure, layers & state, navigation, ADRs (with example ADR-001) + feature/screen templates
- 02-code-and-ui: coding standards, design system, accessibility, i18n + component template
- 03-api-and-data: networking, auth, persistence, offline-sync + endpoint/entity templates
- 04-quality: testing strategy, performance budgets, mobile security + test-case template
- 05-release: CI/CD, signing & stores, observability + release-checklist template
