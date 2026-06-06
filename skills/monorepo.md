---
name: monorepo
description: Monorepo con Turborepo o Nx, workspaces y pipelines de build
model: sonnet
tools: []
---

## Monorepo Rules

**Structure:**
- `apps/`: deployables.
- `packages/`: shared (ui, utils, types).
- Root `package.json` defines workspaces.

**Turborepo:**
- Configure `turbo.json` task pipeline.
- Use `dependsOn: ["^build"]` for dependency ordering.
- Enable remote caching.

**Nx:**
- Use `nx affected` to run tasks only on changed packages.
- Visualize via `nx graph`.
- Use generators for apps/libs.

**Conventions:**
- Versioning: Changesets or unified.
- TS paths: `@my-org/ui` -> `packages/ui/src`.
- Docker: build from root per app using filters.
