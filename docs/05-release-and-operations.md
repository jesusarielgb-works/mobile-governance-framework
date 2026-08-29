# 05 — Release & Operations

## Build

- Reproducible builds from CI only — no store uploads from a developer laptop.
- Separate build flavors/schemes per environment: `dev`, `staging`, `prod`.
- All environment values (base URL, keys, flags) injected at build time — never hardcoded.

## Signing

- Store signing credentials (keystore / provisioning profiles / certificates) in CI secrets,
  never in the repository.
- Android: one release keystore, access restricted. iOS: managed signing with a dedicated
  distribution certificate.
- Rotate credentials on team changes.

## Versioning & Tagging

- Bump SemVer version + build number before every release (see [00 - Governance & Agile](00-governance-and-agile.md)).
- Tag `vX.Y.Z` on `main`; the tag triggers the release pipeline (`.github/workflows/release.yml`).

## CI/CD Pipeline

1. Lint + static analysis.
2. Unit + widget tests.
3. Build signed artifacts (`.apk`/`.aab`, `.ipa`).
4. Distribute to internal testers (Firebase App Distribution / TestFlight).
5. Promote to store review after sign-off.

## Store Distribution

- Ship via **staged rollout** (e.g. 5% → 20% → 100%); halt on a crash/ANR spike.
- Keep store metadata (screenshots, changelog, privacy labels) versioned with the release.
- Maintain the ability to force-update when a release contains a breaking API change.

## Observability

- Integrate crash reporting from day one; track **crash-free users/sessions** (target ≥ 99.5%).
- Capture non-fatal errors and key funnel analytics events.
- Gate risky features behind **feature flags** so they can be disabled without a new release.
- Define rollback: previous build stays available; document the trigger to halt a rollout.
