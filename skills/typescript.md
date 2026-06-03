---
name: typescript
description: TypeScript con strict mode, tipos avanzados y sin any
model: sonnet
tools: []
---

## Technology context — TypeScript (strict mode)

This project uses **TypeScript** with strict configuration.

**tsconfig.json strict:**
- `strict: true` enabled (includes `noImplicitAny`, `strictNullChecks`, `strictFunctionTypes`, etc.)
- `noUncheckedIndexedAccess: true` — array/object access returns `T | undefined`
- `exactOptionalPropertyTypes: true` — distinguishes between `undefined` and absent property

**Advanced types:**
- Use `type` for aliases and unions, `interface` for extensible objects
- `Readonly<T>`, `ReadonlyArray<T>` for immutability
- Template literal types for typed strings: `` `${string}-${number}` ``
- `satisfies` operator to validate without changing the inferred type
- Discriminated unions for exhaustive pattern matching

**No `any`:**
- `unknown` instead of `any` for unknown types — forces validation before use
- Type guards: `typeof`, `instanceof`, predicates `(x): x is T`
- `as` casting only when TypeScript can't infer and you have more information

**Conventions:**
- Explicit return types on public/exported functions
- Descriptive generic names: `TEntity` not `T` in complex contexts
- Enums only when the runtime value matters; otherwise `as const` objects
