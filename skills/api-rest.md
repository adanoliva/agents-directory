---
name: api-rest
description: Diseño de APIs REST — recursos, verbos HTTP, versionado y buenas prácticas
model: sonnet
tools: []
---

## REST API Design Rules

**Resources & URLs:**
- URLs identify **resources** (nouns), not actions: `/users`, `/orders/{id}`.
- Use **plural nouns** for collections: `/articles`, not `/article`.
- Nest sub-resources max 1 level: `/users/{id}/posts` — deeper = separate resource.
- Use kebab-case for multi-word segments: `/payment-methods`.
- Never use verbs in URLs: ❌ `/getUser` — use `GET /users/{id}` instead.

**HTTP Verbs:**
- `GET` — read, idempotent, no side effects.
- `POST` — create a resource or trigger an action.
- `PUT` — full replacement of a resource.
- `PATCH` — partial update (JSON Merge Patch or JSON Patch).
- `DELETE` — remove a resource; idempotent (200 or 404 both valid).

**Status Codes:**
- `200 OK`, `201 Created` (with `Location` header), `204 No Content`.
- `400 Bad Request` (validation), `401 Unauthorized`, `403 Forbidden`, `404 Not Found`.
- `409 Conflict` (duplicate), `422 Unprocessable Entity` (semantic errors).
- `429 Too Many Requests`, `500 Internal Server Error`.

**Request & Response:**
- Always return JSON with `Content-Type: application/json`.
- Error responses: `{ "error": { "code": "VALIDATION_ERROR", "message": "...", "details": [] } }`.
- Use **pagination**: `?page=1&limit=20` or cursor-based. Always return total count.
- Use **filtering**: `?status=active&sort=createdAt:desc`.

**Versioning:**
- Version via URL path: `/v1/users` — easiest to route and cache.
- Never remove fields in the same version; add new ones only.
- Deprecate with `Deprecation` and `Sunset` headers.

**Security:**
- Require authentication on every endpoint unless explicitly public.
- Use HTTPS only. Set `Strict-Transport-Security`.
- Rate-limit all endpoints; return `429` with `Retry-After` header.
