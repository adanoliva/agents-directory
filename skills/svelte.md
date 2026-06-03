---
name: svelte
description: Svelte 5 con runes y SvelteKit
model: sonnet
tools: []
---

## Technology context — Svelte 5

This project uses **Svelte 5** with the new runes system.

- `$state()` for reactive state (replaces reactive `let` from Svelte 4)
- `$derived()` for computed values (replaces `$:`)
- `$effect()` for effects with cleanup (replaces `onMount`/`onDestroy` for reactivity)
- `$props()` to declare typed component props
- **SvelteKit** as meta-framework: file-based routing, load functions, form actions

**Conventions:**
- One component per `.svelte` file
- Svelte stores for shared global state (`writable`, `readable`, `derived`)
- CSS scoped by default in `<style>` — use `:global()` sparingly
- TypeScript in `<script lang="ts">`
