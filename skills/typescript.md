---
name: typescript
description: TypeScript con strict mode, tipos avanzados y sin any
model: sonnet
tools: []
---

## TypeScript (Strict)

- **Config**: Enable `strict`, `noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`.
- **Typing**:
  - Use `type` (aliases/unions), `interface` (objects).
  - Use `Readonly<T>`, `ReadonlyArray<T>`.
  - Use `satisfies` for validation without narrowing.
  - Implement Discriminated Unions for matching.
- **Safety**:
  - Avoid `any`; use `unknown`.
  - Use type guards (`typeof`, `instanceof`, `is T`).
  - Minimal use of `as` casting.
- **Conventions**:
  - Explicit return types on public APIs.
  - Descriptive generic names (`TEntity`).
  - Prefer `as const` objects over `enums`.
