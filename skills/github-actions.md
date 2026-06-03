---
name: github-actions
description: GitHub Actions para CI/CD con jobs, matrices y reusable workflows
model: sonnet
tools: []
---

## Technology context — GitHub Actions

This project uses **GitHub Actions** for CI/CD.

**Workflow structure:**
- `.github/workflows/` for all workflows
- `on:` triggers: `push`, `pull_request`, `schedule`, `workflow_dispatch`
- Jobs parallel by default, `needs:` for inter-job dependencies
- `environment:` for deployments with approvals and environment-specific secrets

**Best practices:**
- Pin action versions with full SHA: `uses: actions/checkout@a5ac7e51b41094c92402da3b24376905380afc29`
- Minimal permissions: `permissions:` at the highest applicable level, restrictive by default
- Secrets in GitHub Secrets, never hardcoded
- Cache: `actions/cache` for `node_modules`, `.gradle`, etc.

**Optimization:**
- `concurrency:` to cancel previous runs for the same PR
- `paths:` filters to skip CI on doc-only changes
- Matrices for tests across multiple versions/OS
- `timeout-minutes:` on jobs to prevent hanging builds

**Common patterns:**
```yaml
- uses: actions/checkout@v4
- uses: actions/setup-node@v4
  with:
    node-version-file: '.nvmrc'
    cache: 'npm'
```

Reusable workflows with `workflow_call` for DRY across repositories.
