# 02 — Code & UI Standards

## Coding Best Practices

- **Immutability first** — prefer immutable models and `const`/`final`/`val` over mutable state.
- **Naming**: `PascalCase` types, `camelCase` members, `UPPER_SNAKE_CASE` constants.
- **Small units** — a function does one thing; a file declares one primary type.
- **No magic values** — extract to named constants or design tokens.
- **Fail fast** — validate inputs at boundaries; never swallow errors silently.
- **Async discipline** — always handle the error branch; cancel work when a screen is disposed.
- **Lint is law** — the project ships with a linter config; CI fails on warnings.

## Error Handling

- Wrap fallible operations in a typed result (`Result`/`Either`) or well-defined exceptions.
- Map low-level errors (network, parsing) to domain errors before they reach the UI.
- Every user-facing failure has a message and a recovery action (retry, dismiss).

## Design System

- Centralize **design tokens** (colors, spacing, radius, typography) in `core/theme/`.
- Build screens from a shared component library — no one-off styled widgets.
- Support light and dark themes from the same token set.
- Respect platform conventions (back navigation, safe areas, gestures).

## Accessibility (required)

- Every interactive element has an accessible label.
- Minimum touch target: 44×44 pt (iOS) / 48×48 dp (Android).
- Text scales with the OS font-size setting; never hardcode absolute font sizes for body text.
- Color contrast meets WCAG AA (4.5:1 for body text).
- Screens are navigable and readable by the platform screen reader (VoiceOver / TalkBack).

## Internationalization (i18n)

- No hardcoded user-facing strings — all copy comes from resource/localization files.
- Format dates, numbers, and currency with locale-aware APIs.
- Support RTL layouts by using start/end (not left/right) for directional spacing.
