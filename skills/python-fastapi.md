---
name: python-fastapi
description: FastAPI con Pydantic v2, async/await y SQLAlchemy
model: sonnet
tools: []
---

## Technology context — Python + FastAPI

This project uses **FastAPI** with Python 3.11+.

- Async endpoints by default: `async def` for I/O, `def` only for CPU-bound work
- **Pydantic v2** for request/response schema validation
- Dependency injection with `Depends()` for: DB sessions, auth, services
- Type hints throughout — no `Any` without justification
- SQLAlchemy 2.x with `AsyncSession` for async database operations

**Structure:**
- `routers/` to group endpoints by domain
- `schemas/` for Pydantic request/response models
- `models/` for SQLAlchemy models
- `services/` for business logic
- `dependencies/` for shared dependencies

**Conventions:**
- Explicit `response_model` on every endpoint
- HTTP exceptions with `HTTPException(status_code=..., detail=...)`
- Background tasks with `BackgroundTasks` for non-critical operations
- Settings with `pydantic-settings` from environment variables
