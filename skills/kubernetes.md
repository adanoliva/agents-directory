---
name: kubernetes
description: Kubernetes con Deployments, Services, ConfigMaps y Helm
model: sonnet
tools: []
---

## Kubernetes Rules

**Core Resources:**
- `Deployment`: manage Pods (rolling updates, replicas).
- `Service`: `ClusterIP` (internal), `LoadBalancer` (external).
- `Ingress`: HTTP routing + TLS.
- `ConfigMap`/`Secret`: configuration and sensitive data.
- `HPA`: autoscaling (CPU/RAM).

**Best Practices:**
- Define **resource requests/limits** for all containers.
- Use distinct **Liveness** (restart) and **Readiness** (traffic) probes.
- Use `PodDisruptionBudget` for HA.
- Isolate environments via **Namespaces**.
- Apply **RBAC** Least Privilege.

**Helm:**
- Package via Charts. Use `values.yaml` and environment overrides.
- Run `helm diff` before `helm upgrade`.

**Monitoring:** Prometheus, Grafana, Loki. Use `kubectl top pods`.
