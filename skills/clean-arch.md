---
name: clean-arch
description: Clean Architecture — capas, dependencias invertidas y casos de uso
model: sonnet
tools: []
---

## Clean Architecture Rules

**Layer Dependency Rule:**
- Dependencies point **inward only**: Infrastructure → Application → Domain.
- Domain has zero external dependencies (no framework, no ORM, no HTTP).
- Application layer depends only on Domain — never on Infrastructure.
- Infrastructure implements interfaces defined in the inner layers.

**Domain Layer:**
- Contains **Entities**, **Value Objects**, **Domain Events**, **Repository interfaces**.
- Business rules and invariants live here — enforce them in constructors/factory methods.
- No `null` returns — use `Option/Maybe` or throw domain exceptions.
- Value Objects are immutable; Entities have identity.

**Application Layer:**
- Contains **Use Cases** (one class per use case): `CreateUser`, `PlaceOrder`.
- Use Cases orchestrate Domain objects and call Repository interfaces.
- Input: **Command/Query DTOs**. Output: **Result DTOs** (no Domain objects leak out).
- Use **CQRS** separation: Commands mutate state, Queries return read models.

**Infrastructure Layer:**
- Contains repository implementations, ORMs, HTTP clients, email senders, etc.
- Adapts external APIs to interfaces defined in the Application or Domain layer.
- Maps between Domain models and persistence/DTO models explicitly.

**Naming Convention:**
- Use Cases: verb + noun (`CreateUserUseCase`, `GetOrderById`).
- Repository interfaces: `IUserRepository` (or `UserRepository` as abstract class).
- Infrastructure implementations: `PostgresUserRepository`, `RedisSessionStore`.

**Testing:**
- Domain: pure unit tests, no mocks needed.
- Application: mock repository interfaces — fast, isolated.
- Infrastructure: integration tests against real DB/services.
