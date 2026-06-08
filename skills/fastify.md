---
name: fastify
description: Fastify con TypeScript, plugins, schemas JSON y validación nativa
model: sonnet
tools: []
---

## Fastify Rules

**Core:**
- Register routes via **plugins** (`fastify.register(plugin, opts)`).
- Encapsulate scope with `fastify-plugin` only when sharing decorators across plugins.
- Use `fastify.decorate` / `decorateRequest` for shared utilities.
- Prefer `async/await`; never mix callbacks and promises.

**Schemas & Validation:**
- Define **JSON Schema** for every route: `schema: { body, querystring, params, response }`.
- Use `$ref` and `addSchema` to share schemas across routes.
- Enable `ajv` strict mode; disable `coerceTypes` unless explicitly needed.
- Always define `response[200]` — it serializes output and strips extra fields.

**Error Handling:**
- Use `fastify.setErrorHandler` for global error formatting.
- Throw `fastify.httpErrors.badRequest('msg')` (via `@fastify/sensible`).
- Never leak stack traces in production responses.

**Plugins to use:**
- `@fastify/sensible` — httpErrors, assert.
- `@fastify/jwt` or `@fastify/oauth2` — auth.
- `@fastify/rate-limit` — rate limiting.
- `@fastify/swagger` — auto-generate OpenAPI from schemas.

**Performance:**
- Avoid synchronous I/O inside route handlers.
- Use `fastify.log` (pino) — never `console.log`.
- Return serializable plain objects from handlers.
