---
name: drizzle
description: Drizzle ORM con TypeScript, migraciones y query builder tipado
model: sonnet
tools: []
---

## Drizzle ORM Rules

**Schema:**
- Define schema in `src/db/schema.ts` (or per-domain files re-exported from an index).
- Use `pgTable` / `mysqlTable` / `sqliteTable` matching your DB.
- Always define `primaryKey`, `notNull`, `defaultNow()` where appropriate.
- Use `relations()` to declare relationships — Drizzle does not auto-infer them.

**Migrations:**
- Generate migrations with `drizzle-kit generate` — never write SQL migrations by hand.
- Apply with `drizzle-kit migrate` or `db.migrate()` in a startup script.
- Commit generated SQL files to version control.

**Queries:**
- Prefer **prepared statements** (`db.select().from(table).prepare('name')`) for repeated queries.
- Use `.where(eq(table.col, val))` — avoid raw string interpolation in conditions.
- For complex joins, use `leftJoin`/`innerJoin` with explicit `on` conditions.
- Use `db.transaction(async (tx) => { ... })` for multi-step operations.

**Type Safety:**
- Infer types with `typeof table.$inferSelect` and `typeof table.$inferInsert`.
- Use `InferSelectModel` / `InferInsertModel` for external type exports.

**Performance:**
- Use `.limit()` and `.offset()` for pagination — never fetch unbounded rows.
- Index foreign keys and frequently filtered columns via `index()` in schema.
