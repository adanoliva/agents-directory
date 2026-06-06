---
name: redis
description: Redis para caché, sesiones, colas y pub/sub  
model: sonnet
tools: []
---

## Redis Rules (v7+)

**Core Uses:**
- **Cache**: `SET key value EX ttl`. Always use explicit TTL.
- **Sessions**: JSON serialization + TTL.
- **Rate limiting**: `INCR` + `EXPIRE` or sorted sets.
- **Pub/Sub**: `PUBLISH`/`SUBSCRIBE` (no guaranteed delivery).
- **Queues**: `RPUSH`/`BLPOP` (simple) or **Redis Streams** (durable).

**Structures:**
- `STRING` (cache/counters), `HASH` (objects), `LIST` (queues), `SET` (unique/M2M), `SORTED SET` (priorities/indexes).

**Best Practices:**
- Namespace keys: `service:entity:id`.
- Use `SCAN` instead of `KEYS *`.
- Use connection pooling.
- Persistence: RDB (snapshots) or AOF (durability).
