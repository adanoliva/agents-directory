---
name: vanilla
description: JavaScript puro con Web APIs y Custom Elements
model: sonnet
tools: []
---

## Technology context — Vanilla JS / Web Components

This project uses **JavaScript or TypeScript without a UI framework**.

- **Web Components**: Custom Elements v1, Shadow DOM, HTML Templates
- Direct DOM API: `querySelector`, `createElement`, event delegation
- Native ES Modules: `import/export` without a bundler or with a minimal one
- Fetch API for HTTP, with AbortController for cancellation

**Patterns:**
- Components as Custom Elements extending `HTMLElement`
- `connectedCallback` / `disconnectedCallback` for lifecycle
- `attributeChangedCallback` with `observedAttributes` for simple reactivity
- Custom events (`CustomEvent`) for component-to-component communication
- No third-party UI dependencies — the web platform only

**Performance:**
- Avoid DOM manipulation in loops — use DocumentFragment
- IntersectionObserver for lazy loading
- requestAnimationFrame for animations
