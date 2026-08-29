# 03 — API & Data Rules

Covers how the app talks to backends (API) and how it stores state locally (data).

## API / Networking

- Single configured HTTP client in `core/network/` — base URL, timeouts, and interceptors
  defined once.
- **Timeouts** on every request (connect + read). No unbounded calls.
- **Retries** only on idempotent requests (GET), with exponential backoff and a max cap.
- Serialize/deserialize through DTOs; map DTO → domain entity in the data layer. The UI
  never sees a raw API payload.
- Handle HTTP status ranges explicitly: 2xx success, 4xx domain/validation error, 5xx
  transient error (retry/backoff).

## Authentication

- Store tokens in the platform **secure storage** (Keychain / Keystore) — never in plain
  preferences or local files.
- Attach the access token via an interceptor, not per-call.
- Refresh expired tokens transparently; on refresh failure, sign the user out cleanly.
- Never log tokens, credentials, or full auth headers.

## Persistence (local database)

- Choose one local store per app (SQLite/Room/Drift, Realm, or a key-value store) and wrap
  it behind a repository interface.
- **Table/entity naming**: snake_case, plural tables; `id` primary key; `created_at` /
  `updated_at` timestamps where records mutate.
- Keep persisted models separate from domain entities; map between them.
- Store only what the app needs offline — do not mirror the entire backend.

## Migrations

- Every schema change ships a versioned migration — never mutate an existing one.
- Migrations are forward-only and tested against a populated database.
- Bump the local schema version on every structural change.

## Offline & Sync

- Define per-feature: read-through cache, offline-first, or online-only. Document the choice.
- For offline-first: queue local mutations and reconcile on reconnect with a clear conflict
  policy (last-write-wins or server-wins).
- Show sync/staleness state in the UI when data may be out of date.
