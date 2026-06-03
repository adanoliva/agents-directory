---
name: tailwind
description: TailwindCSS utility-first con configuración personalizada
model: sonnet
tools: []
---

## Technology context — TailwindCSS

This project uses **TailwindCSS** as the styling system.

- Utility-first: compose classes directly in HTML/JSX/templates
- Responsive design: `sm:`, `md:`, `lg:`, `xl:`, `2xl:` mobile-first prefixes
- Dark mode: with `dark:` class (mode `class` or `media` per config)
- States: `hover:`, `focus:`, `active:`, `disabled:`, `group-hover:`

**Organization:**
- Reusable classes extracted into components, not `@apply` (except for integration with existing CSS)
- `tailwind.config.js` to extend colors, typography and spacing for the design system
- `clsx` or `cn()` helper for conditional classes
- Plugins: `@tailwindcss/forms`, `@tailwindcss/typography` if installed

**Avoid:**
- `!important` via the `!` prefix except in extreme cases
- Arbitrary classes `[value]` for values that should be in the config
