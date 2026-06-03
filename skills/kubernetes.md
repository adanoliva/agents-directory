---
name: kubernetes
description: Kubernetes con Deployments, Services, ConfigMaps y Helm
model: sonnet
tools: []
---

## Technology context — Kubernetes

This project uses **Kubernetes** (K8s).

**Core resources:**
- `Deployment`: manages Pods with rolling updates, rollback and replicas
- `Service`: ClusterIP for internal, LoadBalancer for external, NodePort for dev
- `Ingress`: HTTP/S routing with TLS termination
- `ConfigMap`: non-sensitive configuration
- `Secret`: sensitive data (base64 encoded, or better with external-secrets)
- `HPA`: autoscaling based on CPU/RAM or custom metrics

**Best practices:**
- Resource requests and limits on all containers — without them the scheduler can't plan correctly
- Liveness and readiness probes: keep them distinct — readiness controls traffic, liveness controls restart
- `PodDisruptionBudget` for high availability during cluster upgrades
- Namespaces for environment isolation (dev/staging/prod)
- RBAC: least privilege for service accounts

**Helm:**
- Charts for packaging manifests with variables
- `values.yaml` for defaults, `values-prod.yaml` for production overrides
- `helm diff` before `helm upgrade`

**Monitoring:**
- Prometheus + Grafana for metrics
- Loki for logs
- `kubectl top pods` for real-time resource usage
