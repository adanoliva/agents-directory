---
name: vue
description: Vue 3 con Composition API, TypeScript y Pinia
model: sonnet
tools: []
---

## Technology context — Vue 3

This project uses **Vue 3** with Composition API and TypeScript.

- `<script setup>` as the standard component format
- `ref()` for primitives, `reactive()` for complex objects, `computed()` for derived values
- `watch` and `watchEffect` with cleanup when applicable
- Global state: **Pinia** (not Vuex) — modular stores with typed actions, getters and state
- Routing: Vue Router 4 with route lazy loading
- `defineProps` and `defineEmits` with explicit typing

**Conventions:**
- Component names in PascalCase
- Composables in `use*.ts` for reusable logic
- Named slots for container components
- `v-model` for two-way binding in forms
