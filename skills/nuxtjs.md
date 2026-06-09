---
name: nuxtjs
description: Nuxt 3 con auto-imports, Nitro y composables
model: sonnet
tools: []
---

## Nuxt 3 Rules

**Core:**
- Use **Auto-imports** for `~/composables/`, `~/components/`, `~/utils/`.
- **Nitro** engine: API in `~/server/api/`, middleware in `~/server/middleware/`.
- Data fetching: `useFetch`, `useAsyncData`.
- State: `useState()` (SSR-aware), Pinia (complex).
- Routing: `~/pages/*.vue`, layouts in `~/layouts/`.

**Conventions:**
- Config: `useRuntimeConfig()` (prefix `NUXT_PUBLIC_` for client).
- Plugins in `~/plugins/`.
- Composable naming: `~/composables/use*.ts`.
