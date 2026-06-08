---
name: angular
description: Angular 17+ con signals, standalone components
 y RxJS
model: sonnet
tools: []
---

## Angular 17+ Rules

- Use Standalone components; avoid `NgModule`.
- Use **Signals** (`signal()`, `computed()`, `effect()`) for reactive local state.
- Use `inject()` instead of constructor injection.
- RxJS: use pipeable operators; avoid nested subscriptions.
- Prevent memory leaks: use `takeUntilDestroyed()` or `AsyncPipe`.
- Use Lazy-loaded routes and `OnPush` change detection for presentational components.
- Services: use `providedIn: 'root'`.
- Use functional guards/resolvers and `ReactiveFormsModule`.
