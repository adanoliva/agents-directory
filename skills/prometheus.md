---
name: prometheus
description: Prometheus + Grafana para métricas, alertas y observabilidad
model: sonnet
tools: []
---

## Prometheus + Grafana Rules

**Instrumentation:**
- Expose a `/metrics` endpoint in every service (Prometheus format).
- Use the official client library for your language (`prom-client`, `prometheus-client`, etc.).
- Follow metric naming: `{namespace}_{subsystem}_{name}_{unit}` (e.g., `http_requests_total`).
- Use the correct type: **Counter** (only increases), **Gauge** (up/down), **Histogram** (distributions).

**Metric Design:**
- Add labels for dimensions you'll filter/group by: `method`, `status_code`, `endpoint`.
- Keep label cardinality low — avoid user IDs, UUIDs, or free-text as labels.
- Use Histograms (not Summaries) for latency — they allow aggregation across instances.
- Expose the standard `process_*` and `go_*` / `nodejs_*` metrics via the client library.

**Alerting (Alertmanager):**
- Write alert rules in `alerts.yaml`; group related rules by service.
- Use `for: 5m` to avoid flapping on transient spikes.
- Route alerts by severity: `critical` → PagerDuty, `warning` → Slack.
- Add `runbook_url` annotation to every alert.

**Grafana Dashboards:**
- Store dashboard JSON in version control (`dashboards/`); provision via config.
- Use template variables (`$instance`, `$job`) to make dashboards reusable.
- Golden signals per service: latency (p50/p95/p99), error rate, throughput, saturation.
- Set refresh to 30s for operational dashboards; use longer intervals for capacity.

**Retention & Storage:**
- Default retention: 15d local. For long-term, use **Thanos** or **Cortex**.
- Use `recording rules` for expensive queries that power dashboards.
