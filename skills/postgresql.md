---
name: postgresql
description: PostgreSQL con índices, JSONB, full-text search y optimización
model: sonnet
tools: []
---

## PostgreSQL Rules (v15+)

**Types & Indexes:**
- Types: `UUID`, `TIMESTAMPTZ`, `JSONB`.
- Indexes: B-tree (default), GIN (JSONB/Full-text), BRIN (large append-only).
- Analyze: `EXPLAIN (ANALYZE, BUFFERS)`.
- Patterns: CTEs (`WITH`), Window functions (`ROW_NUMBER`, `LAG`).

**Features:**
- `JSONB` operators: `->`, `->>`, `@>`, `?`.
- Full-text search: `tsvector`, `tsquery`.
- `UPSERT`: `ON CONFLICT DO UPDATE`.
- `LISTEN/NOTIFY` for IPC.

**Best Practices:**
- Keep transactions short.
- Use PgBouncer for pooling.
- Configure Auto-vacuum for high-write tables.
