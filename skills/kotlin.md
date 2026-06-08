---
name: kotlin
description: Kotlin con Jetpack Compose, Hilt y Coroutines 
model: sonnet
tools: []
---

## Kotlin & Jetpack Compose Rules

**Framework:**
- Use **Jetpack Compose** (declarative UI).
- Use **Hilt** for DI (`@HiltViewModel`, `@Inject`).
- Concurrency: **Coroutines + Flow** (`viewModelScope.launch`, `StateFlow`).
- Use **Navigation Compose** for routing.

**Architecture (MVVM):**
- `ViewModel`: `StateFlow<UiState>` + `UiEvent`.
- `Repository`: abstract data (API + local).
- Use **Room** (local) and **Retrofit** (HTTP).

**Compose:**
- State: `remember`, `rememberSaveable`.
- Effects: `LaunchedEffect` (side effects), `DisposableEffect` (cleanup).
- Lists: `LazyColumn`/`LazyRow` with explicit `key`.
- Modifiers order: size -> padding -> background -> clip -> clickable.

**Testing:** `composeTestRule`, `Turbine` (Flow), `MockK`.
