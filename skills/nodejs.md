---
name: nodejs
description: Node.js con Express, TypeScript y arquitectura en capas
model: sonnet
tools: []
---

## Node.js + Express Rules

**Architecture:**
- Layers: `routes` -> `controllers` -> `services` -> `repositories`.
- Express 4/5 + TypeScript (`@types/express`).
- Middleware for auth, validation (`zod`/`joi`), error handling, logging, CORS.

**Patterns:**
- Centralized error handling: middleware with `(err, req, res, next)`.
- Async: use `express-async-errors` or wrappers.
- Logging: use `pino` or `winston` (avoid `console.log`).
- Config: use `dotenv` and a config module (don't access `process.env` directly).

**Testing:** `jest` + `supertest` for endpoints.
