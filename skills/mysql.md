---
name: mysql
description: MySQL 8 / MariaDB con InnoDB, índices y optimización de queries
model: sonnet
tools: []
---

## Technology context — MySQL / MariaDB

This project uses **MySQL 8** or **MariaDB 10.6+**.

- InnoDB engine for all tables (transactional support, FK, row-level locking)
- `utf8mb4` as default charset (not `utf8`, which is only 3 bytes)
- `DATETIME` with timezone managed in the application; `TIMESTAMP` for audit dates
- Composite indexes in the correct order: equality columns first, range columns after

**Optimization:**
- `EXPLAIN` to see the execution plan — look for `type: ref` or better, avoid `ALL`
- Covering indexes for frequent queries: include all columns from the SELECT
- `LIMIT` with keyset pagination for large datasets
- Avoid functions on indexed columns in WHERE (`WHERE YEAR(created_at) = 2024` blocks the index)

**Conventions:**
- FK constraints enabled with explicit `ON DELETE` and `ON UPDATE`
- Table names in snake_case, singular
- Versioned and reversible migrations
- Session variables: `sql_mode` with `STRICT_TRANS_TABLES` enabled
