---
name: monorepo
description: Monorepo con Turborepo o Nx, workspaces y pipelines de build
model: sonnet
tools: []
---

## Technology context — Monorepo

This project uses a **monorepo** managed with Turborepo or Nx.

**Structure:**
- `apps/`: deployable applications (web, api, mobile)
- `packages/`: shared libraries (ui, utils, config, types)
- Root `package.json` with defined workspaces
- `turbo.json` or `nx.json` to define the task pipeline

**Turborepo:**
- `turbo run build` runs builds in parallel respecting dependencies
- `outputs` configured for remote caching (Vercel Remote Cache or equivalent)
- `dependsOn` to order tasks: `["^build"]` means "build dependencies first"

**Nx:**
- `nx affected --target=test` to run only what's affected by changes
- `nx graph` to visualize the dependency graph
- Generators to create apps and libraries with standardized conventions

**Conventions:**
- Independent versioning per package or unified with Changesets
- TypeScript paths to import between packages: `@my-org/ui` → `packages/ui/src`
- Tests and lint run only on the package affected by the PR
- Dockerfile per app, build from monorepo root with `--filter`
