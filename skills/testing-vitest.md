---
name: testing-vitest
description: Vitest para tests unitarios y de integración en proyectos Vite
model: sonnet
tools: []
---

## Technology context — Vitest

This project uses **Vitest** as the testing framework.

- Jest-compatible API: `describe`, `it`/`test`, `expect`, `vi` (equivalent to `jest`)
- Configuration in `vite.config.ts` under the `test:` key — shares Vite config
- Native ESM without transformation — faster than Jest in modern projects
- Hot module replacement in watch mode — relevant tests re-run instantly

**Mocking API:**
- `vi.mock('module')` for module mocks
- `vi.spyOn(object, 'method')` to spy on methods
- `vi.fn()` for mock functions
- `vi.useFakeTimers()` and `vi.advanceTimersByTime()` for time control
- `vi.stubEnv('VAR', 'value')` for environment variables in tests

**Recommended configuration:**
```ts
// vite.config.ts
test: {
  environment: 'jsdom',    // or 'node' for backends
  globals: true,            // describe/it/expect without import
  setupFiles: './src/test/setup.ts',
  coverage: { provider: 'v8' }
}
```

**Testing Library with Vitest:**
- `@testing-library/react` works the same as with Jest
- `@testing-library/vue` and `@testing-library/svelte` available
- `@vitest/ui` for visual test interface in the browser
