---
name: go
description: Go con net/http, Gin/Chi, módulos y patrones idiomáticos
model: sonnet
tools: []
---

## Technology context — Go

This project uses **Go 1.22+**.

- Errors as values — always handle `if err != nil`, never ignore errors with `_`
- Small interfaces: define the interface where it's used, not where it's implemented
- Goroutines and channels for concurrency — `sync.WaitGroup` and `sync.Mutex` when clearer
- Context propagated through all I/O functions: `context.Context` as the first argument

**HTTP:**
- Standard `net/http` for simple APIs
- `chi` or `gin` for routing with middleware when justified
- Middleware as `func(http.Handler) http.Handler`

**Project structure:**
- `/cmd/` for main packages, `/internal/` for private code, `/pkg/` for exportable code
- One package = one responsibility — avoid packages named `utils` or `helpers`
- Configuration via environment variables or flags, not complex config files

**Conventions:**
- `gofmt` and `golangci-lint` — code is formatted automatically
- Tests in `*_test.go` alongside the code they test
- Table-driven tests with `t.Run()`
- Documentation for exported functions with `// FuncName ...` comment
