---
name: rust
description: Rust con Tokio, Axum y ownership idiomático  
model: sonnet
tools: []
---

## Rust Rules (2021 Edition)

**Core:**
- Handle ownership/borrowing; avoid thoughtless `.clone()`.
- Error handling: use `Result<T, E>`/`Option<T>`. Never `.unwrap()` in production; use `?`.
- Use `thiserror` (custom errors) or `anyhow` (binaries).
- Async: use **Tokio** and `async/await`.

**Web:**
- Framework: **Axum** (routers, extractors, layers).
- Serialization: `serde` + `serde_json`.
- Database: `sqlx` (compile-time checked async SQL).
- Middleware: use `tower` layers.

**Conventions:**
- Zero warnings in `clippy`; auto-format with `rustfmt`.
- Inline tests: `#[cfg(test)]`.
- Document public items: `///`.
- Minimize shared state; use `Arc<Mutex<T>>` sparingly.
