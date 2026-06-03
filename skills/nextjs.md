---
name: nextjs
description: Next.js 14 con App Router, Server Components y Server Actions
model: sonnet
tools: []
---

## Technology context — Next.js 14 App Router

This project uses **Next.js 14** with the App Router.

- **Server Components** by default — add `"use client"` only when you need interactivity or browser APIs
- **Server Actions** for data mutations from forms and events
- `fetch` with cache options: `{ cache: 'force-cache' }`, `{ next: { revalidate: N } }` or `{ cache: 'no-store' }`
- Nested layouts in `layout.tsx`, loading states in `loading.tsx`, errors in `error.tsx`
- Metadata API for SEO: `export const metadata` or `generateMetadata()`
- Image optimization with `next/image`, font optimization with `next/font`

**Routing:**
- Dynamic routes: `[slug]`, route groups: `(group)`, parallel routes: `@slot`
- Intercepting routes: `(.)`, `(..)` for modals and overlays
- Middleware for authentication and redirects

**Data:**
- Load data directly in Server Components (async/await)
- `use()` hook to read promises in Client Components
