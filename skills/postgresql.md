---
name: postgresql
description: PostgreSQL con índices, JSONB, full-text search y optimización
model: sonnet
tools: []
---

## Technology context — PostgreSQL

This project uses **PostgreSQL 15+**.

- Appropriate data types: `UUID`, `TIMESTAMPTZ` (with timezone), `JSONB` for semi-structured data
- Indexes: B-tree by default, GIN for JSONB and full-text, BRIN for timestamp columns in append-only tables
- `EXPLAIN (ANALYZE, BUFFERS)` to understand execution plans
- CTEs (`WITH`) for readable complex queries
- Window functions (`ROW_NUMBER`, `RANK`, `LAG`, `LEAD`) for analytics

**PostgreSQL-specific features:**
- `JSONB` with operators `->`, `->>`, `@>`, `?` for semi-structured data
- Full-text search: `tsvector`, `tsquery`, `GIN` index
- Table partitioning by range or hash for very large tables
- `UPSERT` with `ON CONFLICT DO UPDATE`
- `LISTEN/NOTIFY` for inter-process communication

**Best practices:**
- Short transactions — don't do slow operations inside a transaction
- Connection pooling with PgBouncer in production
- Auto-vacuum configured appropriately for high-write tables
