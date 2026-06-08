---
name: github-actions
description: GitHub Actions para CI/CD con jobs, matrices y reusable workflows
model: sonnet
tools: []
---

## GitHub Actions Rules

**Structure:**
- Define workflows in `.github/workflows/`.
- Use `on:` triggers (`push`, `pull_request`, `workflow_dispatch`).
- Parallel jobs by default; use `needs:` for dependencies.
- Use `environment:` for deployments + approvals.

**Best Practices:**
- Pin actions with **full SHA**.
- Minimal `permissions:`.
- Use GitHub Secrets for sensitive data.
- Use `actions/cache` for dependencies.

**Optimization:**
- `concurrency:` to cancel redundant runs.
- `paths:` to skip CI on docs.
- Use `matrices` and `timeout-minutes:`.
- Use `workflow_call` for reusable workflows.
