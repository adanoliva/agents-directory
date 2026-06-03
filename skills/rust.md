---
name: rust
description: Rust con Tokio, Axum y ownership idiomático
model: sonnet
tools: []
---

## Technology context — Rust

This project uses **Rust (2021 edition)**.

- Explicit ownership and borrowing — don't use `.clone()` to dodge the borrow checker without thinking
- `Result<T, E>` and `Option<T>` — never `.unwrap()` in production code, use `?` or explicit handling
- `thiserror` for custom error types, `anyhow` for error handling in binaries
- **Tokio** as async runtime, `async/await` for non-blocking I/O

**Web:**
- **Axum** as HTTP framework: routers, extractors, layers (middleware)
- `serde` + `serde_json` for serialization
- `sqlx` for async SQL queries with compile-time checking
- `tower` layers for reusable middleware

**Conventions:**
- `clippy` with no warnings, `rustfmt` for formatting
- Inline tests in the module with `#[cfg(test)]`
- Documentation with `///` for public items
- `Arc<Mutex<T>>` sparingly — design to minimize shared state

**Structure:**
- `src/main.rs` or `src/lib.rs` as entry point
- Modules in `src/` organized by domain
- `Cargo.workspace` for monorepos
