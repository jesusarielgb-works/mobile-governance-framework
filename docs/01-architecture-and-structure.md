# 01 — Architecture & Structure

## Project Layout (feature-first)

Organize by **feature**, not by technical type. Each feature owns its layers.

```
lib|src/
├── core/                 Shared utilities, theme, DI, base classes
│   ├── di/               Dependency injection setup
│   ├── network/          HTTP client, interceptors
│   └── theme/            Design tokens, typography
├── features/
│   └── <feature>/
│       ├── presentation/ Screens, widgets/views, state (ViewModel/Bloc/Store)
│       ├── domain/       Entities, use cases, repository interfaces
│       └── data/         Repository impl, data sources, DTOs, mappers
└── app.<ext>             Root widget/app, routing table
```

- One feature = one folder. No cross-feature imports except through `core/`.
- Filename matches the primary type it declares.

## Layers

| Layer | Responsibility | Allowed Dependencies |
|-------|----------------|----------------------|
| Presentation | Render UI, hold view state, dispatch intents | Domain |
| Domain | Use cases, entities, repository interfaces | None |
| Data | Repository impls, remote/local sources, mapping | Domain |

## Dependency Direction

```
Presentation -> Domain <- Data
```

Domain has zero outward dependencies and knows nothing about the framework, HTTP, or the
database. Presentation never imports a data source directly — it goes through a use case
or repository interface.

## State Management

- Pick **one** unidirectional pattern per app: MVVM (ViewModel + observable state), MVI
  (intent → reducer → state), or Bloc/Redux-style store. Do not mix patterns.
- View state is immutable; screens render a single state object.
- No business logic in widgets/views — delegate to the ViewModel/use case.

## Navigation

- Centralize routes in one declarative routing table.
- Navigate by named route or typed destination — never construct screens ad hoc deep in the tree.
- Pass identifiers, not full objects, across routes; re-fetch in the destination.

## Dependency Injection

- All dependencies constructed in `core/di/` and injected via constructors.
- No global singletons or service-locator lookups inside domain/presentation code.
- Provide interfaces (domain) and bind implementations (data) at the composition root.
