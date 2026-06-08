---
name: supabase
description: Supabase con Auth, Postgres, Storage, Realtime y Edge Functions
model: sonnet
tools: []
---

## Supabase Rules

**Client Setup:**
- Use `createClient` with env vars `SUPABASE_URL` and `SUPABASE_ANON_KEY`.
- Server-side operations use the **service role key** — never expose it to the client.
- Use `@supabase/ssr` helpers for server-rendered frameworks (Next.js, SvelteKit).

**Database:**
- All schema changes via **migrations** (`supabase/migrations/`). Never alter prod manually.
- Enable **Row Level Security (RLS)** on every table — no exceptions.
- Write explicit policies: `FOR SELECT`, `FOR INSERT`, `FOR UPDATE`, `FOR DELETE`.
- Use Postgres functions for complex logic that needs to bypass RLS safely.
- Prefer `supabase.from('table').select('col1, col2')` over `select('*')`.

**Auth:**
- Use `supabase.auth.getUser()` on the server (verifies JWT); `getSession()` on client only.
- Protect routes by checking `user` in middleware/layout — never trust the client.
- Store user metadata in a `profiles` table linked to `auth.users` via trigger.

**Storage:**
- Use signed URLs for private buckets; public URLs only for truly public assets.
- Set bucket policies to restrict file types and sizes.

**Edge Functions:**
- Use Deno runtime — no `require`, use `import`.
- Validate the `Authorization` header before any business logic.
- Keep functions small and single-purpose.

**Realtime:**
- Subscribe only to necessary channels; unsubscribe on component unmount.
- Use `postgres_changes` for DB events; broadcast for ephemeral messages.
