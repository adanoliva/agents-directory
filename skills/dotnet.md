---
name: dotnet
description: .NET 8 con ASP.NET Core, minimal APIs y Entity Framework
model: sonnet
tools: []
---

## .NET Rules

**Core:**
- Use **.NET 8+** and C# 12.
- Prefer **Minimal APIs** for simple services.
- Use **EF Core** (Code-First + Migrations).
- Use native DI; avoid manual registration.
- Log via `ILogger<T>`.
- Use **Records** (DTOs) and **sealed classes**.

**Patterns:**
- EF `DbContext` as Unit of Work.
- Use MediatR for CQRS if requested.
- Use `Result<T>` or `OneOf` for error handling.
- Use FluentValidation and `CancellationToken` in I/O.

**Conventions:**
- Enable **Nullable reference types**.
- Use `appsettings.json` and `IOptions<T>`.
