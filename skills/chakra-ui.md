---
name: chakra-ui
description: Chakra UI v3 con sistema de tokens, recetas y slot recipes
model: sonnet
tools: []
---

## Chakra UI v3 Rules

**Setup:**
- Use `ChakraProvider` with `createSystem(defaultConfig, { ... })`.
- Build systems using `defineConfig` (replaces v2 `theme`).

**Styling:**
- Use style props: `color`, `bg`, `px`, etc.
- Prefer semantic tokens: `fg.muted`, `bg.subtle`, `border.muted`.
- Use pseudo-states: `_hover`, `_focus`, `_active`, `_disabled`.
- Dark mode: use `_dark` prop (e.g., `color={{ base: "black", _dark: "white" }}`).
- No inline `style={{}}`; use props or recipes.

**Layout:**
- Use `Stack`, `HStack`, `VStack`, `Grid`, and `Flex`.
- Use `Box` as a generic container.

**Recipes:**
- Define custom components with `defineRecipe` (variants, sizes, defaultVariants).
- Use **Slot recipes** for multi-part components (Card, Tabs, Dialog).

**Forms:**
- Use `Field`, `Input`, `Select`, `Textarea` with `invalid` prop.
- Use `FieldLabel`, `FieldErrorText`, `FieldHelperText`.

**Conventions:**
- Use `colorPalette` for themed component families.
- Responsive logic: use `useBreakpointValue` or object notation in props `px={{ base: 2, md: 4 }}`.
