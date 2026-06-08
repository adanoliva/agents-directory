---
name: prisma
description: Prisma ORM con TypeScript, migraciones y cliente tipado
model: sonnet
tools: []
---

## Prisma Rules

**Setup:**
- Schema: `prisma/schema.prisma` (source of truth).
- CLI: `prisma migrate dev` (dev), `prisma migrate deploy` (prod).
- Run `prisma generate` after schema changes.

**Usage:**
- Use a **shared PrismaClient instance** (singleton).
- Use `$transaction()` (interactive or batch) for atomicity.
- Use `select` to limit columns; use `include` for relations.
- Filter with `in` instead of loops.

**Best Practices:**
- PascalCase for models; camelCase for fields.
- Use `@default(now())` and `@updatedAt`.
- Use `prisma db seed`.
- Pagination: use `take` and `skip` or cursor-based.
- Single-run scripts: call `$connect()` and `$disconnect()`.
