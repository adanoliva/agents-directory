---
name: svelte
description: Svelte 5 con runes y SvelteKit
model: sonnet
tools: []
---

## Svelte 5 Rules

**Runes System:**
- `$state()`: reactive state.
- `$derived()`: computed values.
- `$effect()`: effects + cleanup.
- `$props()`: typed component props.

**SvelteKit:**
- File-based routing.
- Use `load` functions and form actions.

**Conventions:**
- One component per `.svelte` file.
- Global State: use Svelte stores (`writable`, `readable`, `derived`).
- Scoped CSS: use `<style>`; use `:global()` sparingly.
- Use `<script lang="ts">`.
