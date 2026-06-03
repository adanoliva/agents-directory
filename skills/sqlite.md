---
name: sqlite
description: SQLite para apps embebidas, desktop y proyectos ligeros
model: sonnet
tools: []
---

## Technology context — SQLite

This project uses **SQLite 3.x**.

- Embedded database: single file, no server, ideal for desktop and edge
- WAL mode enabled: `PRAGMA journal_mode=WAL` — better performance for concurrent reads
- `PRAGMA foreign_keys=ON` — FKs are not validated by default
- `PRAGMA synchronous=NORMAL` for balance between durability and performance

**Limitations to keep in mind:**
- Blocking writes: only one writer at a time — design for short writes
- Dynamic typing: SQLite uses type affinity, not strict types — be explicit in code
- No full `ALTER TABLE`: to change columns, recreate the table
- No `RIGHT JOIN` or `FULL OUTER JOIN` (in older versions)

**Optimization:**
- `EXPLAIN QUERY PLAN` to check if indexes are used
- Indexes on frequently searched columns and JOINs
- Explicit transactions for batch inserts (dramatically faster)
- Periodic `VACUUM` to reclaim space

**Production use:**
- Backup with SQLite Online Backup API or `VACUUM INTO`
- Litestream for continuous replication to S3
