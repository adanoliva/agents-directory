---
name: go
description: Go con net/http, Gin/Chi, módulos y patrones idiomáticos
model: sonnet
tools: []
---

## Go Rules (v1.22+)

- Handle all errors: `if err != nil`. Never ignore with `_`.
- Define small interfaces where used.
- Concurrency: use Goroutines/Channels; `sync.WaitGroup`/`sync.Mutex` for clarity.
- Propagate `context.Context` as the first argument in I/O functions.

**HTTP & API:**
- Use `net/http` for simple APIs; `chi` or `gin` for routing/middleware.
- Middleware format: `func(http.Handler) http.Handler`.

**Project Structure:**
- `/cmd/`: main. `/internal/`: private. `/pkg/`: exportable.
- One package = one responsibility (avoid `utils`/`helpers`).
- Use environment variables/flags for config.

**Conventions:**
- Auto-format with `gofmt` and `golangci-lint`.
- Tests in `*_test.go` using table-driven patterns (`t.Run()`).
- Document exported functions: `// FuncName ...`.
