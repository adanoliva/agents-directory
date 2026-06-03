---
name: react
description: React 18 con TypeScript, hooks y patrones modernos
model: sonnet
tools: []
---

## Technology context — React 18

This project uses **React 18** with TypeScript.

- Functional components with hooks — never classes
- Local state: `useState`, `useReducer` for complex state
- Effects: `useEffect` with explicit cleanup, precise dependencies
- Memoization: `useMemo` and `useCallback` only when the profiler shows a real gain
- Context for component-tree state; global state library for application-wide data
- Concurrent features: `startTransition` for non-urgent updates, `Suspense` for async loading
- `StrictMode` enabled in development

**Preferred patterns:**
- Composition over prop drilling
- Custom hooks for reusable logic
- Error boundaries for fault isolation
- Fragments when no DOM wrapper is needed
