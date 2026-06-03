---
name: swift
description: Swift 5.9+ con SwiftUI, Combine y Swift Concurrency
model: sonnet
tools: []
---

## Technology context — Swift / SwiftUI

This project uses **Swift 5.9+** with **SwiftUI**.

- **Swift Concurrency**: `async/await`, `Task`, `actor` for concurrent state
- `@Observable` macro (iOS 17+) or `ObservableObject` + `@Published` for reactive state
- `@StateObject` for ownership, `@ObservedObject` for references, `@EnvironmentObject` for injection
- Combine for complex data streams (though Swift Concurrency is gradually replacing it)

**Architecture:**
- MVVM with ViewModels as `@Observable` classes
- Views contain no business logic — presentation only
- Repositories for data source abstraction (network, Core Data, UserDefaults)

**SwiftUI:**
- Lightweight composable struct views
- `PreviewProvider` for Xcode canvas previews
- `LazyVStack` / `LazyHStack` for long lists
- Environment values for theming and localization

**Best practices:**
- `Sendable` protocol for types crossing concurrency domains
- `MainActor` for UI updates from async tasks
- `@Sendable` closures
- Avoid `DispatchQueue` directly — use `Task` and `actor`
