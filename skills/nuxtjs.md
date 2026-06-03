---
name: nuxtjs
description: Nuxt 3 con auto-imports, Nitro y composables
model: sonnet
tools: []
---

## Technology context — Nuxt 3

This project uses **Nuxt 3**.

- Auto-imports: composables from `~/composables/`, components from `~/components/` and utils from `~/utils/` without explicit imports
- **Nitro** as server engine: API routes in `~/server/api/`, middleware in `~/server/middleware/`
- `useFetch` and `useAsyncData` for unified SSR/CSR data fetching
- Global state: `useState()` for SSR-aware state, Pinia for complex stores
- File-based routing: `~/pages/*.vue`, layouts in `~/layouts/`

**Conventions:**
- `useRuntimeConfig()` for environment variables (private on server, public with `NUXT_PUBLIC_` prefix)
- Plugins in `~/plugins/` for third-party libraries
- `~/composables/use*.ts` for reusable logic
- Nitro routes: `GET`, `POST`, etc. exported from `~/server/api/[name].ts`
