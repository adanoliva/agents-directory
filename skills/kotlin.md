---
name: kotlin
description: Kotlin con Jetpack Compose, Hilt y Coroutines
model: sonnet
tools: []
---

## Technology context — Kotlin / Jetpack Compose

This project uses **Kotlin** with **Jetpack Compose**.

- **Jetpack Compose**: declarative UI, composables as functions annotated with `@Composable`
- **Hilt** for dependency injection — `@HiltViewModel`, `@Inject`, `@Singleton`
- **Coroutines + Flow**: `viewModelScope.launch`, `StateFlow` for UI state, `SharedFlow` for events
- **Navigation Compose**: `NavController`, `composable { }` destinations, safe args

**Architecture (MVVM + Repository):**
- `ViewModel`: exposes `StateFlow<UiState>` and handles `UiEvent`
- `Repository`: abstracts data sources (API + local database)
- `Room` for local persistence with typed DAO interfaces
- `Retrofit` + `OkHttp` for HTTP with interceptors for auth and logging

**Compose:**
- `remember` and `rememberSaveable` for local state
- `LaunchedEffect` for side effects with key, `DisposableEffect` for cleanup
- `LazyColumn` / `LazyRow` for lists with explicit `key`
- Modifiers chained in order: size → padding → background → clip → clickable

**Testing:**
- `composeTestRule` for composable UI tests
- `Turbine` for Flow tests
- `MockK` for idiomatic Kotlin mocking
