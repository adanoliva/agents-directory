---
name: mysql
description: MySQL 8 / MariaDB con InnoDB, índices y optimización de queries
model: sonnet
tools: []
---

## MySQL / MariaDB Rules

**Config & Design:**
- Engine: **InnoDB** (all tables).
- Charset: **utf8mb4**.
- Time: `DATETIME` (app-managed) or `TIMESTAMP` (audit).
- Use **snake_case** singular for table names.
- Enable `STRICT_TRANS_TABLES`.

**Optimization:**
- Analyze with `EXPLAIN`. Avoid `type: ALL`.
- Composite indexes: equality columns first, then ranges.
- Use covering indexes for frequent queries.
- Pagination: keyset (via `LIMIT`) for large sets.
- No functions on indexed columns in `WHERE`.

**Data Integrity:**
- Enable FK constraints with explicit `ON DELETE/UPDATE`.
- Use versioned, reversible migrations.
