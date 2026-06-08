---
name: kafka
description: Apache Kafka — productores, consumidores, topics y patrones de mensajería
model: sonnet
tools: []
---

## Apache Kafka Rules

**Topics & Partitions:**
- Name topics descriptively: `{domain}.{entity}.{event}` (e.g., `orders.order.placed`).
- Choose partition count based on target throughput and consumer parallelism.
- Set retention by time (`retention.ms`) or size (`retention.bytes`) — not both.
- Use **compacted topics** for changelog/state (latest value per key is kept).

**Producers:**
- Set `acks=all` for durability (all ISR replicas must acknowledge).
- Enable **idempotent producer** (`enable.idempotence=true`) to prevent duplicates.
- Use **transactions** (`transactional.id`) for exactly-once across multiple topics.
- Set appropriate `batch.size` and `linger.ms` to balance latency vs. throughput.
- Handle `ProducerRecord` keys deliberately — null key = round-robin partition, keyed = sticky partition.

**Consumers:**
- Use **consumer groups** for horizontal scaling — one group per application.
- Commit offsets **after** processing, not before — prefer manual commit.
- Handle **rebalances** with `ConsumerRebalanceListener` (pause, flush, then rejoin).
- Design consumers to be **idempotent** — at-least-once delivery is the default.
- Set `max.poll.interval.ms` to exceed your longest processing time.

**Schema & Contracts:**
- Use **Avro/Protobuf** with **Schema Registry** — never raw JSON in production.
- Evolve schemas with backward/forward compatibility rules.

**Operations:**
- Monitor: consumer lag, under-replicated partitions, broker disk usage.
- Use **Kafka Connect** for source/sink integrations — don't write custom connectors.
- Set `min.insync.replicas=2` with replication factor ≥ 3 for durability.
