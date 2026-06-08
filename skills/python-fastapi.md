---
name: python-fastapi
description: FastAPI con Pydantic v2, async/await y SQLAlchemy
model: sonnet
tools: []
---

## FastAPI Rules (Python 3.11+)

**Core:**
- Use `async def` for I/O; `def` for CPU-bound tasks.
- Use **Pydantic v2** for validation.
- DI: use `Depends()` for DB, auth, and services.
- Database: **SQLAlchemy 2.x** with `AsyncSession`.
- Strict typing: no `Any` without justification.

**Structure:**
- `/routers/` (domain), `/schemas/` (Pydantic), `/models/` (SQLAlchemy), `/services/` (logic).

**Conventions:**
- Required `response_model` on every endpoint.
- Use `HTTPException` for errors.
- Use `BackgroundTasks` for non-critical async work.
- Use `pydantic-settings` for env config.
