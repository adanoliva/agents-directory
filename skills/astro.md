---
name: astro
description: Astro con islands architecture, SSG/SSR, integraciones y Content Collections
model: sonnet
tools: []
---

## Astro Rules

**Core Concepts:**
- Default to **zero JS** — ship static HTML unless interactivity is needed.
- Use **Islands** (`client:load`, `client:idle`, `client:visible`) only for interactive components.
- Prefer `client:idle` and `client:visible` over `client:load` to defer hydration.
- Use `.astro` components for layout/static content; UI framework components only for islands.

**Routing & Pages:**
- File-based routing under `src/pages/`. Dynamic routes use `[param].astro`.
- Use `getStaticPaths()` for SSG dynamic routes; `output: 'server'` for full SSR.
- API routes live in `src/pages/api/` — return `Response` objects.

**Content Collections:**
- Define collections in `src/content/config.ts` with Zod schemas.
- Use `getCollection()` and `getEntry()` — never `fs.readdir` manually.
- Frontmatter is type-safe; validate on build, not at runtime.

**Performance:**
- Use `<Image />` from `astro:assets` for all images (auto-optimization).
- Avoid importing heavy JS in `.astro` frontmatter — it ships to the server only.
- Inline critical CSS; use `<style>` blocks (scoped by default).

**Integrations:**
- Add integrations in `astro.config.mjs` — `@astrojs/react`, `@astrojs/tailwind`, etc.
- Use adapters (`@astrojs/vercel`, `@astrojs/node`) for SSR deployments.
