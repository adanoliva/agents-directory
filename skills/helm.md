---
name: helm
description: Helm 3 para gestión de paquetes Kubernetes con charts y values tipados
model: sonnet
tools: []
---

## Helm Rules

**Chart Structure:**
- Follow standard layout: `Chart.yaml`, `values.yaml`, `templates/`, `charts/`.
- Keep `Chart.yaml` accurate: `appVersion` = app version, `version` = chart version (SemVer).
- Use `_helpers.tpl` for shared template fragments (`fullname`, `labels`, `selector`).

**Values:**
- Document every value in `values.yaml` with inline comments.
- Use nested keys for logical grouping: `image.repository`, `image.tag`, `resources.limits`.
- Never hardcode image tags in templates — always `{{ .Values.image.tag | quote }}`.
- Provide sane defaults; override per environment in separate `values-{env}.yaml` files.

**Templates:**
- Use `{{ include "chart.fullname" . }}` — avoid duplicating name logic.
- Set standard labels on every resource:
  ```yaml
  labels: {{ include "chart.labels" . | nindent 4 }}
  ```
- Use `tpl` function for values that need template rendering.
- Validate with `helm lint` before pushing — enforce in CI.

**Dependencies:**
- Pin dependency versions in `Chart.yaml`; commit `Chart.lock`.
- Use `helm dependency update` to fetch deps; never commit the `charts/` directory.

**Releases:**
- Use `helm upgrade --install` for idempotent CI deployments.
- Set `--atomic` in CI to auto-rollback on failed deployments.
- Store releases in a dedicated namespace per environment.
- Use `helm test` to run post-deploy smoke tests.
