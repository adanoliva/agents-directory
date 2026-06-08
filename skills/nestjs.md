---
name: nestjs
description: NestJS con TypeScript, módulos, decoradores e inyección de dependencias
model: sonnet
tools: []
---

## NestJS Rules

**Architecture:**
- Organize by **feature modules** (`@Module`). One module per domain.
- Use **dependency injection** via constructor; avoid manual `new`.
- Prefer `Injectable` services over fat controllers.
- Separate concerns: Controller (HTTP) → Service (logic) → Repository (data).

**Controllers & Routes:**
- Use `@Controller('resource')` + HTTP decorators (`@Get`, `@Post`, `@Put`, `@Delete`).
- Use `@Body()`, `@Param()`, `@Query()` — never `req.body` directly.
- Validate all inputs with **class-validator** + `ValidationPipe` globally.
- Use `@HttpCode()` and `@HttpException` for explicit status codes.

**DTOs & Validation:**
- All request bodies use **DTOs** with `class-validator` decorators.
- Enable `transform: true` in `ValidationPipe` for automatic type coercion.
- Use `@PartialType(CreateDto)` for update DTOs.

**Guards, Interceptors & Pipes:**
- Auth via `@UseGuards(JwtAuthGuard)` — apply globally when possible.
- Use `@UseInterceptors(ClassSerializerInterceptor)` to strip sensitive fields.
- Custom exceptions extend `HttpException` with meaningful messages.

**Config & Env:**
- Use `@nestjs/config` with a typed config service.
- Never access `process.env` directly in services — inject `ConfigService`.
