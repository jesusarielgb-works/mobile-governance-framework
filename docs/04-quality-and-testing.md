# 04 — Quality & Testing

## Test Pyramid

| Type | Scope | Speed | Share |
|------|-------|-------|-------|
| Unit | Use cases, ViewModels, mappers — no UI, no I/O | Fast | ~70% |
| Widget / UI | A single screen/component in isolation | Medium | ~20% |
| Integration / E2E | Full flow on a simulator/emulator or device | Slow | ~10% |

## Rules

- Every use case and ViewModel has unit tests; mock only direct dependencies.
- Test behavior and state transitions, not implementation details.
- Naming: `<unit>_<condition>_<expectedResult>` — e.g. `login_whenTokenExpired_showsError`.
- Arrange-Act-Assert; keep tests deterministic (no real network, no wall-clock sleeps).
- Coverage target: **80% minimum** on `domain/` (use cases) and ViewModels.
- CI runs the full unit + widget suite on every PR; E2E runs on a nightly/pre-release job.

## Performance Budgets

Set and enforce budgets; regressions fail the build or the release checklist.

| Metric | Budget (guideline) |
|--------|--------------------|
| Cold start to first frame | ≤ 2 s |
| Frame rendering | 60 fps, no jank on scroll |
| App install size | Tracked; justify any increase |
| Memory on core flows | No leaks; stable under navigation churn |

- Profile with the platform tools before optimizing; measure, don't guess.
- Lazy-load heavy screens and images; paginate long lists.

## Mobile Security

- Secrets and tokens only in secure storage (Keychain / Keystore).
- Enforce TLS; enable certificate pinning for sensitive APIs.
- Request the minimum set of runtime permissions, just-in-time, with rationale.
- Obfuscate/minify release builds; strip logs from release.
- Never ship API keys or credentials in the repository or the bundle.
