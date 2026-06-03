---
name: redis
description: Redis para caché, sesiones, colas y pub/sub
model: sonnet
tools: []
---

## Technology context — Redis

This project uses **Redis 7+**.

- **Cache**: `SET key value EX ttl` — always with explicit TTL, never infinite cache without justification
- **Sessions**: session storage with JSON serialization and TTL aligned with the session
- **Rate limiting**: `INCR` + `EXPIRE` or sorted sets for sliding windows
- **Pub/Sub**: `PUBLISH` / `SUBSCRIBE` for real-time notifications — no guaranteed delivery
- **Queues**: `RPUSH` / `BLPOP` for simple queues; **Redis Streams** for greater durability

**Data structures:**
- `STRING`: simple cache, counters
- `HASH`: partially updatable objects
- `LIST`: queues, recent activity logs
- `SET`: unique membership, many-to-many relationships
- `SORTED SET`: leaderboards, priorities, time-based indexes

**Best practices:**
- Key namespacing: `service:entity:id` (e.g. `user:session:123`)
- Avoid `KEYS *` in production — use `SCAN` with cursor
- Persistence: RDB for snapshots, AOF for greater durability (evaluate the tradeoff)
- Connection pooling — don't open one connection per request
