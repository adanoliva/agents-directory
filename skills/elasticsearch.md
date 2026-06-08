---
name: elasticsearch
description: Elasticsearch con mappings, queries DSL, índices y buenas prácticas
model: sonnet
tools: []
---

## Elasticsearch Rules

**Index Design:**
- Define explicit **mappings** before indexing — never rely on dynamic mapping in production.
- Use `keyword` for exact match/aggregations, `text` for full-text search.
- Disable `_source` only when storage is critical and you don't need original docs.
- Use **ILM (Index Lifecycle Management)** for time-based indices (logs, events).
- Set `number_of_shards` based on expected data volume (start with 1 for <50GB).

**Mappings:**
- Set `index: false` on fields never queried to save space.
- Use `eager_global_ordinals: true` on `keyword` fields used in frequent aggregations.
- Map dates with explicit `format`; map geo with `geo_point` type.

**Queries:**
- Use `filter` context (not `query`) for exact matches — results are cached, no scoring.
- Use `bool` query to combine `must`, `should`, `filter`, `must_not`.
- Avoid `wildcard` and `regexp` on leading wildcards — extremely slow.
- Use `search_after` for deep pagination instead of `from/size` beyond 10k docs.
- Set `_source: ['field1', 'field2']` to fetch only needed fields.

**Performance:**
- Bulk index with the **Bulk API** — never index documents one by one.
- Refresh interval: set to `30s` or `1m` for write-heavy workloads (not `1s` default).
- Use **aliases** for index management — zero-downtime reindexing.

**Operations:**
- Monitor **heap usage** (keep below 50% of JVM heap), **disk watermarks**, and **shard count**.
- Snapshot to S3/GCS daily with SLM (Snapshot Lifecycle Management).
- Enable **security**: TLS + authentication — never expose Elasticsearch publicly.
