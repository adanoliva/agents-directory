---
name: tailwind
description: TailwindCSS utility-first con configuración personalizada
model: sonnet
tools: []
---

## TailwindCSS

- **Utilities**: Compose classes in HTML/JSX.
- **Responsive**: Use mobile-first prefixes (`sm:`, `md:`, `lg:`, etc.).
- **States**: Use `dark:`, `hover:`, `focus:`, `active:`, `group-hover:`.
- **Organization**:
  - Extract reusable classes into components.
  - Avoid `@apply` (unless integrating legacy CSS).
  - Use `tailwind.config.js` for design system extensions.
  - Use `clsx` or `cn()` for conditionals.
- **Constraints**:
  - Avoid `!important` (`!`).
  - Avoid arbitrary values `[value]`; add to config instead.
