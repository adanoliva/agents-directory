---
name: mongodb
description: MongoDB con Mongoose, aggregation pipeline e índices
model: sonnet
tools: []
---

## Technology context — MongoDB

This project uses **MongoDB 7+**.

- Document design driven by access patterns, not relational normalization
- Embedded vs. referenced: embed when you read the full document most of the time, reference when subdocuments are large or queried independently
- Indexes: compound indexes with most selective fields first, text indexes for search
- `explain("executionStats")` to analyze execution plans

**Aggregation Pipeline:**
- Preferred over client-side JS for aggregations — processes on the server
- `$match` and `$project` at the start to reduce documents early
- `$lookup` for joins — use sparingly (signal that you might need references)
- `$facet` for multiple aggregations in a single query

**Mongoose (if applicable):**
- Strict schemas with model-level validation
- Virtuals for computed unpersisted fields
- Middleware (pre/post hooks) for cross-cutting logic
- `lean()` on read-only queries for better performance

**Best practices:**
- Appropriate write concerns for durability (`{w: 'majority'}` in production)
- Multi-document transactions only when strictly necessary (they have a cost)
