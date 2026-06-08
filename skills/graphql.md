---
name: graphql
description: GraphQL API con schema-first o code-first, resolvers y DataLoader
model: sonnet
tools: []
---

## GraphQL Rules

**Schema Design:**
- Use **code-first** (decorators) or **schema-first** (SDL) consistently — don't mix.
- Name types in PascalCase, fields in camelCase, enums in SCREAMING_SNAKE_CASE.
- Use `input` types for mutations — never reuse query types as mutation args.
- Prefer **nullable fields by default**; use `!` only for guaranteed values.
- Paginate collections with **Relay cursor pagination** (`edges/node/pageInfo`).

**Resolvers:**
- Keep resolvers thin — delegate to service layer.
- Use **DataLoader** to batch and cache per-request (N+1 prevention).
- Return `null` for missing optional data; throw `GraphQLError` for hard errors.
- Use `@ResolveField` for computed/related fields.

**Mutations:**
- Mutations return the mutated object (or a payload type with `userErrors[]`).
- Use descriptive names: `createPost`, `updatePost`, `deletePost`.
- Validate inputs before touching the DB; surface errors in `userErrors`.

**Performance:**
- Implement **query complexity** and **depth limits**.
- Use **persisted queries** in production.
- Cache at field level with `@CacheControl` when applicable.

**Security:**
- Disable introspection in production.
- Never expose internal IDs — use opaque global IDs (`base64(type:id)`).
