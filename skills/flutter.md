---
name: flutter
description: Flutter con Riverpod, Dart null safety y go_router
model: sonnet
tools: []
---

## Flutter Rules

**Framework:**
- Use **Riverpod** (code gen) + `@riverpod`.
- Use **go_router** for navigation.
- Use `const` widgets and `ListView.builder`/`GridView.builder`.
- Use `AsyncValue<T>` for states (loading/error/data).
- Repositories for data abstraction.

**Dart:**
- Use **Freezed** for immutable/unions.
- Strict **Null Safety**: no `!` without justification; use `??` and `?.`.
- Use `sealed class` (Dart 3) for exhaustive states.
- Use named constructors (`ClassName.fromJson`).

**Testing:**
- `flutter_test` (unit/widget), `integration_test` (E2E).
- Use `mockito` or `mocktail`.
