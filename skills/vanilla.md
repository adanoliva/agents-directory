---
name: vanilla
description: JavaScript puro con Web APIs y Custom Elements
model: sonnet
tools: []
---

## Vanilla JS / Web Components

- **Tech**: Custom Elements v1, Shadow DOM, HTML Templates, ES Modules.
- **APIs**: `querySelector`, `createElement`, Fetch API + `AbortController`. Use event delegation.
- **Components**:
  - Extend `HTMLElement`.
  - Use `connectedCallback`/`disconnectedCallback`.
  - Use `attributeChangedCallback` + `observedAttributes` for reactivity.
  - Use `CustomEvent` for communication.
- **Constraints**: No UI frameworks or third-party UI dependencies.
- **Performance**: Use `DocumentFragment` for batch DOM ops. Use `IntersectionObserver` (lazy load) and `requestAnimationFrame`.
