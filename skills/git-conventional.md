---
name: git-conventional
description: Conventional Commits para historial semántico y changelogs automáticos
model: sonnet
tools: []
---

## Conventional Commits Rules

**Format:** `<type>(<scope>): <description>`

**Types:**
- `feat`: new feature (MINOR)
- `fix`: bug fix (PATCH)
- `feat!`/`fix!`: BREAKING CHANGE (MAJOR)
- `refactor`, `docs`, `test`, `chore`, `perf`, `style`, `ci`.

**Rules:**
- Use **present imperative**: "add feature" (not "added").
- No period at end of subject.
- Scope optional: `feat(auth):`.
- Document breaking changes in footer: `BREAKING CHANGE: <desc>`.

**Tools:** `commitlint`, `semantic-release`, `conventional-changelog`.
