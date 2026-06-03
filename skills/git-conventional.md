---
name: git-conventional
description: Conventional Commits para historial semántico y changelogs automáticos
model: sonnet
tools: []
---

## Technology context — Conventional Commits

This project uses **Conventional Commits** as the commit message format.

**Format:**
```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

**Types:**
- `feat`: new feature (MINOR in semver)
- `fix`: bug fix (PATCH in semver)
- `feat!` or `fix!` or `BREAKING CHANGE:` in footer: API-breaking change (MAJOR in semver)
- `refactor`: code change without changing functionality or fixing a bug
- `docs`: documentation changes only
- `test`: add or modify tests
- `chore`: maintenance tasks (deps, build, config)
- `perf`: performance improvement
- `style`: formatting, whitespace, semicolons (no logic change)
- `ci`: changes to CI/CD files

**Rules:**
- Description in present imperative: "add feature" not "added feature"
- No period at end of subject line
- Optional scope in parentheses: `feat(auth):`, `fix(api):`
- Breaking changes documented in footer: `BREAKING CHANGE: description`

**Tooling:**
- `commitlint` to validate in pre-commit hook
- `semantic-release` or `release-please` for automated releases
- `conventional-changelog` to generate CHANGELOG.md
