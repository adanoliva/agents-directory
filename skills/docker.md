---
name: docker
description: Docker con multi-stage builds, Docker Compose y buenas prácticas
model: sonnet
tools: []
---

## Technology context — Docker + Compose

This project uses **Docker** with **Docker Compose**.

**Dockerfiles:**
- Multi-stage builds: separate build stage from final image (smaller size)
- Non-root user: `USER node` or `USER appuser` before CMD
- Optimized layers: `COPY package*.json` before source code for dependency caching
- Complete `.dockerignore`: exclude `node_modules`, `.git`, dev files

**Base images:**
- Alpine for small images when there are no incompatibilities
- `distroless` for maximum production security (no shell)
- Pin exact versions: `node:20.11.0-alpine` not `node:latest`

**Docker Compose:**
- `compose.yml` (new format, no `version:`) for development environments
- `healthcheck` on services that others depend on
- `depends_on` with `condition: service_healthy` for correct startup order
- Variables in `.env` with documented `.env.example`

**Networks and volumes:**
- Named volumes for persistent data, bind mounts for code in development
- Custom networks to isolate services — don't expose unnecessary ports to the host
