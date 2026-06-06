---
name: mui
description: MUI v6 con sistema sx, temas y componentes de Material Design
model: sonnet
tools: []
---

## Material UI (MUI) v6 Rules

**Styling:**
- Use `sx` prop for one-offs.
- Use `styled()` for re-usable components.
- Use theme keys in `sx`: `color: 'text.secondary'`, `bgcolor: 'background.paper'`.
- Use `sx={{ mt: 2 }}` (8px scale); no inline `style={{ marginTop: '16px' }}`.
- Never override `.Mui*` classes directly; use the theme.

**Theme:**
- Centralize in `createTheme()` (palette, typography, components).
- Access via `useTheme()` hook.

**Layout:**
- Use `Box`, `Stack` (linear), `Grid2` (grid), and `Container`.
- `Grid2` usage: `size={{ xs: 12, md: 6 }}`.

**Components:**
- Import icons individually: `import AddIcon from '@mui/icons-material/Add'`.
- `TextField`: always include `label`.
- Modals: use `Dialog` components.
- Forms: controlled `TextField`.

**Conventions:**
- Import from `@mui/material` directly.
- Add variants/colors to theme, not inline.
