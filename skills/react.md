---
name: react
description: React 18 con TypeScript, hooks y patrones modernos
model: sonnet
tools: []
---

## React 18 Rules

**Core:**
- Use **Functional components** and **hooks** (no classes).
- State: `useState`, `useReducer` (complex state).
- Effects: `useEffect` with cleanup and precise dependencies.
- Memoization: `useMemo`/`useCallback` only when profiling justifies it.
- Global State: use Context for tree-state; libraries for app-wide data.
- Concurrent Features: `startTransition`, `Suspense`.

**Patterns:**
- **Composition over prop drilling**.
- Use **Custom hooks** for reusable logic.
- Use **Error boundaries** for fault isolation.
- Use **Fragments** to avoid extra DOM nodes.
- Enable `StrictMode` in development.
