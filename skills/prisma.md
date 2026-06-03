---
name: prisma
description: Prisma ORM con TypeScript, migraciones y cliente tipado
model: sonnet
tools: []
---

## Technology context — Prisma ORM

This project uses **Prisma** with TypeScript.

- Schema in `prisma/schema.prisma` — source of truth for the data model
- `prisma migrate dev` for development migrations, `prisma migrate deploy` in production
- Auto-generated and fully typed Prisma Client
- `prisma generate` required after schema changes

**Usage patterns:**
- One shared `PrismaClient` instance (singleton) — don't instantiate per request
- `$transaction()` for atomic operations: interactive (`$transaction(async (tx) => {...})`) or batch
- Explicit `select` to avoid over-fetching columns
- `include` for needed relations, `select` inside `include` for specific columns

**Best practices:**
- Prisma model names in PascalCase, fields in camelCase — Prisma maps to snake_case in DB
- `@default(now())` and `@updatedAt` for automatic timestamps
- Typed Prisma enums in TypeScript code
- `prisma db seed` with `prisma/seed.ts` for initial data

**Performance:**
- `findMany` with `take` and `skip` or cursor pagination
- Avoid queries inside loops — use `findMany` with `in` filter
- `$connect()` and `$disconnect()` in single-run scripts
