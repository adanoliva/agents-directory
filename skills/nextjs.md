---
name: nextjs
description: Next.js 14 con App Router, Server Components y Server Actions
model: sonnet
tools: []
---

## Next.js 14 Rules (App Router)

- Use **Server Components** by default; `"use client"` only for interactivity/browser APIs.
- Use **Server Actions** for mutations.
- Data fetching: load directly in Server Components (async/await).
- Use `fetch` cache options: `force-cache`, `revalidate: N`, `no-store`.
- Core files: `layout.tsx` (nested layouts), `loading.tsx` (loaders), `error.tsx` (errors).
- Metadata: use `export const metadata` or `generateMetadata()`.
- Optimizers: `next/image` and `next/font`.
- Routing: Dynamic `[slug]`, Groups `(group)`, Parallel `@slot`, Intercepting `(.)`/`(..)`.
- Use Middleware for auth/redirects.
