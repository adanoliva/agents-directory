---
name: flutter
description: Flutter con Riverpod, Dart null safety y go_router
model: sonnet
tools: []
---

## Technology context — Flutter / Dart

This project uses **Flutter 3.x** with **Dart 3** and null safety.

- **Riverpod** (with code gen) as state solution — `@riverpod` annotation for providers
- **go_router** for declarative navigation with deep links and shell routes
- `const` widgets where possible — reduces rebuilds
- `ListView.builder` and `GridView.builder` for long lists (lazy loading)

**Architecture:**
- Feature-first or layer-first depending on project complexity
- `AsyncValue<T>` from Riverpod for loading/error/data states
- Repositories for data source abstraction — injected via Riverpod
- `freezed` for immutable classes and union types

**Dart patterns:**
- Strict null safety: no `!` without justification, use `??` and `?.` for safe chaining
- `sealed class` for exhaustive states (Dart 3)
- Streams for real-time data, Futures for one-time operations
- Named constructors for factories (`ClassName.fromJson`)

**Testing:**
- `flutter_test` for unit and widget tests
- `integration_test` for E2E tests on real device
- `mockito` or `mocktail` for typed mocks
