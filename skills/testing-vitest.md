---
name: testing-vitest
description: Vitest para tests unitarios y de integración en proyectos Vite
model: sonnet
tools: []
---

## Vitest

- **API**: Jest-compatible (`describe`, `test`, `expect`). Use `vi` for mocks.
- **Config**: Defined in `vite.config.ts` (`test:` key). Native ESM support.
- **Mocking**: Use `vi.mock()`, `vi.spyOn()`, `vi.fn()`, `vi.useFakeTimers()`, `vi.stubEnv()`.
- **Ecosystem**:
  - Supports `@testing-library/react`, `vue`, `svelte`.
  - Use `@vitest/ui` for visual interface.
- **Standard Config**:
```ts
test: { environment: 'jsdom', globals: true, setupFiles: './src/test/setup.ts', coverage: { provider: 'v8' } }
```
