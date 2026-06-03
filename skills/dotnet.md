---
name: dotnet
description: .NET 8 con ASP.NET Core, minimal APIs y Entity Framework
model: sonnet
tools: []
---

## Technology context — .NET / C#

This project uses **.NET 8+** with C# 12.

- **ASP.NET Core**: minimal APIs or controllers depending on project complexity
- **Entity Framework Core** with Code-First and migrations
- Native framework Dependency Injection — don't manually register services where DI can infer
- `ILogger<T>` for structured logging
- **Records** for immutable DTOs, **sealed classes** where inheritance isn't needed

**Patterns:**
- Repository pattern optional — EF DbContext is already a Unit of Work
- MediatR for CQRS if the project separates commands/queries
- `Result<T>` or discriminated unions (with OneOf) for error handling without exceptions
- FluentValidation for request validation
- `CancellationToken` in all async methods that do I/O

**Conventions:**
- Nullable reference types enabled (`<Nullable>enable</Nullable>`)
- `appsettings.json` + `appsettings.{Environment}.json` for configuration
- `IOptions<T>` for strongly-typed configuration
