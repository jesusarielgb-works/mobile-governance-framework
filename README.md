# Mobile Governance Framework

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![jesusarielgb-works](https://img.shields.io/badge/org-jesusarielgb--works-blue)](https://github.com/jesusarielgb-works)

> Governance standards and architectural conventions for mobile applications — stack-agnostic (Flutter, React Native, native iOS, native Android).

**Author:** [Jesus Ariel Gonzalez Bonilla](https://github.com/jesusarielgb-works)

## Overview

Defines end-to-end governance standards for teams building mobile apps: agile process,
architecture, coding & UI standards, API & data rules, quality strategy, and release.

The conventions are **stack-agnostic** — examples are neutral and apply whether the app
is built with Flutter, React Native, SwiftUI, or Jetpack Compose. Pick the concrete tool
for each rule inside your own project.

Companions:
[monolith-governance-framework](https://github.com/jesusarielgb-works/monolith-governance-framework) ·
[microservices-governance-framework](https://github.com/jesusarielgb-works/microservices-governance-framework)
(part of [jesusarielgb-works](https://github.com/jesusarielgb-works))

## Sections

The whole framework lives in a single flat `docs/` folder. Read it top to bottom — the
six sections follow the mobile lifecycle end to end.

| Doc | Content |
|-----|---------|
| [00 - Governance & Agile](docs/00-governance-and-agile.md) | Agile process, ceremonies, DoR/DoD, branching, versioning |
| [01 - Architecture & Structure](docs/01-architecture-and-structure.md) | Project layout, layers, MVVM/MVI, state, navigation, DI |
| [02 - Code & UI Standards](docs/02-code-and-ui-standards.md) | Coding best practices, design system, accessibility, i18n |
| [03 - API & Data Rules](docs/03-api-and-data-rules.md) | Networking, auth, error handling, persistence, offline, migrations |
| [04 - Quality & Testing](docs/04-quality-and-testing.md) | Test pyramid, performance budgets, mobile security |
| [05 - Release & Operations](docs/05-release-and-operations.md) | CI/CD, signing, store distribution, observability |

## How to Use

1. **Fork** (or copy the structure) into your project repository.
2. **Read each `docs/` file** in order — they build on one another.
3. **Adapt the neutral rules** to your concrete stack (Flutter / React Native / native).
4. Keep the rules that fit your team; delete what does not apply.

## How to Cite

> Gonzalez Bonilla, J. A. (2026). *Mobile Governance Framework* (v1.0.0). jesusarielgb-works. https://github.com/jesusarielgb-works/mobile-governance-framework

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT — Jesus Ariel Gonzalez Bonilla. See [LICENSE](LICENSE).
