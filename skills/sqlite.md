---
name: sqlite
description: SQLite para apps embebidas, desktop y proyectos ligeros
model: sonnet
tools: []
---

## SQLite Rules (v3.x)

**Config:**
- Enable WAL mode: `PRAGMA journal_mode=WAL`.
- Enable FK: `PRAGMA foreign_keys=ON`.
- Sync: `PRAGMA synchronous=NORMAL`.

**Optimization:**
- Check plans: `EXPLAIN QUERY PLAN`.
- Index frequently searched/joined columns.
- Use **explicit transactions** for batch inserts.
- Periodically run `VACUUM`.

**Limitations:**
- One writer at a time; keep writes short.
- Dynamic typing: be explicit in code.
- No `RIGHT JOIN` or `FULL OUTER JOIN` in old versions.
- Recreate tables to change columns.

**Production:** use `VACUUM INTO` or Litestream (S3 replication).
