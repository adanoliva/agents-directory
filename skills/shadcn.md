---
name: shadcn
description: shadcn/ui con Radix UI, Tailwind y class-variance-authority
model: sonnet
tools: []
---

## shadcn/ui Rules

**Philosophy:**
- Components live in `components/ui/`. You own and modify them.
- Use `npx shadcn@latest add <component>`; never hand-write generated components.

**Stack:**
- **Radix UI** (behavior), **Tailwind CSS** (styles), **cva** (variants).
- Use **`cn()`** (`lib/utils.ts`) for all conditional classes.

**Styling:**
- Colors/Theme: use CSS variables in `globals.css` (`--primary`, etc.).
- Dark mode: uses `.dark` class on root.
- Extend variants in the component file, not ad-hoc.
- Use **`asChild`** (Radix) for polymorphic composition.

**Forms:**
- Use `react-hook-form` + `zod` + shadcn's `<Form>` components.
- Use `FormField`, `FormItem`, `FormLabel`, `FormControl`, `FormMessage`.
