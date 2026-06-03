---
name: nodejs
description: Node.js con Express, TypeScript y arquitectura en capas
model: sonnet
tools: []
---

## Technology context — Node.js + Express

This project uses **Node.js with Express** and TypeScript.

- Express 4/5 typed with `@types/express`
- Layered architecture: `routes` → `controllers` → `services` → `repositories`
- Middleware for: authentication, validation, error handling, logging, CORS
- Request validation: `zod` or `joi` in controllers
- Environment variables: `dotenv` with documented `.env.example`

**Patterns:**
- Centralized error handling: error middleware with `(err, req, res, next)`
- Async/await with `express-async-errors` or wrapper to catch rejected promises
- Logging with `pino` or `winston`, not `console.log` in production
- Typed `process.env` — don't access directly, use a config module

**Testing:**
- `jest` + `supertest` for endpoint integration tests
- Service mocks in controller tests
