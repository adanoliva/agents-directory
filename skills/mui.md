---
name: mui
description: MUI v6 con sistema sx, temas y componentes de Material Design
model: sonnet
tools: []
---

## Technology context — Material UI v6

This project uses **MUI v6** (`@mui/material`).

**Styling system:**
- `sx` prop for one-off styles on a specific component
- `styled()` from `@mui/material/styles` for reusable components with variants
- Don't mix both in the same component — pick one and stay consistent
- Never override generated CSS classes (`.MuiButton-root`) — use the theme system

**Theme:**
- Centralize in `createTheme()` — `palette`, `typography`, `spacing`, `breakpoints` and `components` overrides
- Access tokens in `sx` using theme keys: `color: 'text.secondary'`, `bgcolor: 'background.paper'`
- `useTheme()` hook when you need theme values in JS logic

**Layout:**
- `Box` as a semantic div with `sx`
- `Stack` for linear lists with uniform gap (better than Grid for simple flows)
- `Grid2` (new API) for grid layouts — `size={{ xs: 12, md: 6 }}`
- `Container` for max-width per breakpoint

**Components:**
- Icons from `@mui/icons-material` imported individually: `import AddIcon from '@mui/icons-material/Add'`
- `TextField` always with `label` or `aria-label` — never placeholder-only
- Modals with `Dialog` + `DialogTitle` + `DialogContent` + `DialogActions`
- Forms: controlled `TextField` with `value` + `onChange`, validation outside the component

**Conventions:**
- Don't use `style={{ marginTop: '16px' }}` — use `sx={{ mt: 2 }}` (theme uses 8px scale)
- `variant`, `color` and `size` come from the theme; if you need a new one, add it to the theme, not inline
- Import from `@mui/material` directly, not from internal paths

```tsx
// ✅
<Button variant="contained" color="primary" sx={{ mt: 2 }}>Save</Button>

// ❌
<Button style={{ marginTop: '16px', backgroundColor: '#1976d2' }}>Save</Button>
```
