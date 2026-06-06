---
name: mongodb
description: MongoDB con Mongoose, aggregation pipeline e índices
model: sonnet
tools: []
---

## MongoDB Rules (v7+)

**Design:**
- Driven by access patterns.
- Embed for common reads; reference for large/independent subdocs.
- Indexes: compound (selective fields first), text (search).
- Analyze via `explain("executionStats")`.

**Aggregation Pipeline:**
- Prefer over client-side JS.
- Order: `$match` -> `$project` (early reduction).
- Use `$lookup` sparingly. Use `$facet` for multiple aggregations.

**Mongoose:**
- Use strict schemas and validation.
- Use Virtuals (computed) and Middleware (hooks).
- Use `lean()` for read-only queries.

**Best Practices:**
- Write concern: `{w: 'majority'}` in production.
- Use multi-doc transactions only when essential.
