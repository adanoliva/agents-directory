---
name: microservices
description: Patrones de microservicios — comunicación, resiliencia y datos distribuidos
model: sonnet
tools: []
---

## Microservices Rules

**Service Design:**
- Each service owns **one bounded context** — aligned with a business capability.
- Services are independently deployable; changes to one don't require deploying others.
- Each service has its **own database** — no shared schemas or direct DB access across services.
- Services expose a versioned API; breaking changes require a new version (`/v2/`).

**Communication:**
- **Sync (REST/gRPC):** use for queries where the caller needs an immediate response.
- **Async (message broker):** use for commands and events where eventual consistency is acceptable.
- Never call another service's DB directly — always go through its API.
- Use **circuit breakers** (Resilience4j, Polly) on all sync calls to downstream services.

**Data Consistency:**
- Use **Saga pattern** (choreography or orchestration) for distributed transactions.
- Apply **Outbox pattern** to reliably publish events alongside DB writes.
- Design for **eventual consistency** — UIs should handle stale data gracefully.

**Resiliency:**
- Implement **retries with exponential backoff + jitter** for transient failures.
- Set **timeouts** on every outbound call — never wait indefinitely.
- Use **bulkheads** to isolate failures (separate thread pools per dependency).
- Design services to be **idempotent** — duplicate messages must produce the same result.

**Observability:**
- Propagate **trace IDs** (OpenTelemetry) across all service boundaries.
- Centralize logs with a correlation ID per request.
- Health endpoints: `/health/live` (is the process up?) and `/health/ready` (can it serve traffic?).

**Deployment:**
- Deploy each service in its own container/pod.
- Use feature flags instead of long-lived feature branches.
- Prefer blue/green or canary deployments to reduce blast radius.
