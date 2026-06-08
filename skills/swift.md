---
name: swift
description: Swift 5.9+ con SwiftUI, Combine y Swift Concurrency
model: sonnet
tools: []
---

## Swift / SwiftUI

- **Swift 5.9+**: Use `async/await`, `Task`, `actor` for concurrency.
- **State**: Use `@Observable` (iOS 17+) or `ObservableObject` + `@Published`.
- **Property Wrappers**: Use `@StateObject` (ownership), `@ObservedObject` (reference), `@EnvironmentObject` (injection).
- **Architecture**: MVVM. ViewModels as `@Observable`. Presentation-only Views. Repositories for data abstraction.
- **Views**: Composable structs. Use `PreviewProvider` for previews, `LazyVStack`/`LazyHStack` for lists, Environment for themes.
- **Best Practices**:
  - Implement `Sendable` for cross-concurrency types.
  - Apply `@MainActor` for UI updates.
  - Use `@Sendable` closures.
  - Prefer `Task`/`actor` over `DispatchQueue`.
