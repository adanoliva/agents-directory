---
name: remix
description: Remix con loaders, actions, nested routes y progressive enhancement
model: sonnet
tools: []
---

## Remix Rules

**Routing:**
- File-based nested routing under `app/routes/`. Use `_layout.tsx` for shared layouts.
- Use `$param` for dynamic segments; `($optional)` for optional params.
- Resource routes (API-like) export only `loader`/`action`, no default component.

**Loaders & Actions:**
- `loader` fetches data for GET; `action` handles mutations (POST/PUT/DELETE).
- Always return typed `json()` or `redirect()` — never plain objects.
- Throw `Response` for error cases (`throw new Response('Not Found', { status: 404 })`).
- Use `useLoaderData<typeof loader>()` for fully typed data.

**Forms & Mutations:**
- Use `<Form method="post">` for mutations — native HTML, works without JS.
- Use `useFetcher` for non-navigating mutations (likes, toggles).
- Validate in `action` and return errors as `json({ errors })` — display with `useActionData`.
- Revalidation is automatic after every action — don't manually refresh.

**Error Handling:**
- Add `ErrorBoundary` to every route that fetches data.
- Use `isRouteErrorResponse` to distinguish thrown Responses from unexpected errors.

**Performance:**
- Avoid waterfall fetching — parallel loaders at the route level.
- Use `<Links />` prefetching (`prefetch="intent"` on `<Link>`).
- Keep loaders fast; defer heavy data with `defer()` + `<Await>`.
