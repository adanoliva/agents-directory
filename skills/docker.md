---
name: docker
description: Docker con multi-stage builds, Docker Compose y buenas prácticas
model: sonnet
tools: []
---

## Docker Rules

**Dockerfiles:**
- Use **Multi-stage builds** for smaller images.
- Run as **non-root user** (`USER node`/`appuser`).
- Optimize layers: `COPY package*.json` before source.
- Include complete `.dockerignore` (exclude `node_modules`, `.git`).
- Pin exact versions: `node:20.11.0-alpine` (avoid `latest`).
- Use `alpine` or `distroless` for security/size.

**Docker Compose:**
- Use `compose.yml` (no `version:`).
- Define `healthcheck` and `depends_on` with `condition: service_healthy`.
- Use `.env` and `.env.example`.

**Networking & Volumes:**
- Use named volumes for persistence; bind mounts for dev.
- Isolate services with custom networks.
