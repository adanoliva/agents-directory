---
name: shadcn
description: shadcn/ui con Radix UI, Tailwind y class-variance-authority
model: sonnet
tools: []
---

## Technology context — shadcn/ui

This project uses **shadcn/ui**.

**Key philosophy:** components live in `components/ui/` and are **your code**. They are not an npm dependency — you copy them, own them, and modify them freely.

**Adding components:**
```bash
npx shadcn@latest add button
npx shadcn@latest add dialog card form input
```
Never hand-write what `shadcn add` can generate. Always review the generated code.

**Internal stack:**
- **Radix UI** for behavior and accessibility (Dialog, Popover, Tooltip, Select…)
- **Tailwind CSS** for styles
- **class-variance-authority (`cva`)** for typed variants
- **`cn()`** from `lib/utils.ts` for conditional classes (`clsx` + `tailwind-merge`)

**Variants with `cva`:**
```tsx
const buttonVariants = cva(
  "inline-flex items-center justify-center rounded-md text-sm font-medium transition-colors",
  {
    variants: {
      variant: {
        default:     "bg-primary text-primary-foreground hover:bg-primary/90",
        destructive: "bg-destructive text-destructive-foreground hover:bg-destructive/90",
        outline:     "border border-input bg-background hover:bg-accent",
        ghost:       "hover:bg-accent hover:text-accent-foreground",
      },
      size: {
        default: "h-10 px-4 py-2",
        sm:      "h-9 px-3",
        lg:      "h-11 px-8",
        icon:    "h-10 w-10",
      },
    },
    defaultVariants: { variant: "default", size: "default" },
  }
)
```

**CSS tokens:**
- Colors are CSS variables in `globals.css`: `--background`, `--foreground`, `--primary`, `--muted`…
- Dark mode via `.dark` class on root — `tailwind.config` with `darkMode: ["class"]`
- To change the theme: edit variables in `globals.css`, not component Tailwind classes

**Forms:**
- Always use `react-hook-form` + `zod` + shadcn's `<Form>` — the component already integrates the context
- `FormField`, `FormItem`, `FormLabel`, `FormControl`, `FormMessage` for each field

**Conventions:**
- Extend variants in the component file, not with ad-hoc `className` at each use site
- Use `asChild` from Radix for polymorphic composition without extra DOM wrapper
- `cn()` for all conditional classes — no string concatenation
