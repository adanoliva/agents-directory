---
name: chakra-ui
description: Chakra UI v3 con sistema de tokens, recetas y slot recipes
model: sonnet
tools: []
---

## Technology context — Chakra UI v3

This project uses **Chakra UI v3**.

**Setup:**
- `ChakraProvider` at root with `createSystem(defaultConfig, { ... })` — v3 uses a different token system than v2
- The system replaces v2's `theme` with a `system` built using `defineConfig`

**Style props:**
- All CSS props available directly: `color`, `bg`, `mt`, `px`, `fontSize`, `borderRadius`…
- Semantic tokens preferred over hardcoded values: `color="fg.muted"`, `bg="bg.subtle"`, `borderColor="border.muted"`
- `_hover`, `_focus`, `_active`, `_disabled` for pseudo-states
- `_dark` for declarative dark mode without `useColorMode`: `color={{ base: "black", _dark: "white" }}`

**Layout:**
- `Stack` (vertical), `HStack` (horizontal), `VStack` with `gap` for uniform spacing
- `Grid` with `templateColumns`, `templateRows`
- `Flex` when you need fine control over `flexDirection`, `alignItems`, `justifyContent`
- `Box` as a generic container with all style props

**Recipes (`cva` from Chakra):**
```tsx
import { defineRecipe } from "@chakra-ui/react"

export const buttonRecipe = defineRecipe({
  base: { display: "flex", alignItems: "center" },
  variants: {
    variant: {
      solid:  { bg: "colorPalette.500", color: "white" },
      ghost:  { bg: "transparent", _hover: { bg: "colorPalette.100" } },
    },
    size: {
      sm: { px: 3, py: 1, fontSize: "sm" },
      md: { px: 4, py: 2, fontSize: "md" },
    },
  },
  defaultVariants: { variant: "solid", size: "md" },
})
```

**Slot recipes** for multi-part components (Card, Tabs, Dialog).

**Forms:**
- `Field`, `Input`, `Select`, `Textarea` with `invalid` prop for error states
- `FieldLabel`, `FieldErrorText`, `FieldHelperText` for accessible context

**Conventions:**
- Don't use `style={{}}` inline — everything goes in style props or recipes
- `colorPalette` prop to apply a color to a component's entire family
- Avoid `useColorMode` for styles — use `_dark` directly in props
- `useBreakpointValue` for responsive JS logic; for CSS, style props as objects: `px={{ base: 2, md: 4 }}`
