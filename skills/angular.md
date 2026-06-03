---
name: angular
description: Angular 17+ con signals, standalone components y RxJS
model: sonnet
tools: []
---

## Technology context — Angular 17+

This project uses **Angular 17+**.

- Standalone components — no `NgModule` for new components
- **Signals** for reactive local state: `signal()`, `computed()`, `effect()`
- `inject()` instead of constructor injection where possible
- RxJS for async streams: prefer pipeable operators, avoid nested subscriptions
- Mandatory unsubscribe: `takeUntilDestroyed()` or `AsyncPipe` to prevent memory leaks
- Lazy-loaded routes by default
- OnPush change detection for presentational components

**Conventions:**
- Services as singletons via `providedIn: 'root'`
- Functional guards and resolvers (not classes)
- Reactive forms (`ReactiveFormsModule`) for complex validation
