---
name: cypress
description: Cypress para tests E2E y de componentes con buenas prácticas
model: sonnet
tools: []
---

## Cypress Rules

**Structure:**
- Tests in `cypress/e2e/`; support/commands in `cypress/support/`.
- Use **custom commands** (`cy.login()`, `cy.seedDb()`) to avoid repetition.
- Use Page Object Model for complex UIs — keep test code declarative.

**Selectors:**
- Use `cy.get('[data-cy="submit"]')` as primary selector strategy.
- Fallback to `cy.contains()` for text-based elements.
- Never use CSS classes or positional selectors (`.nth-child`).

**Commands & Assertions:**
- Chain assertions: `cy.get('input').should('have.value', 'foo')`.
- Use `cy.intercept()` to stub/spy network requests — assert on them.
- Use `cy.fixture()` for test data; avoid hardcoded values in tests.
- Avoid `cy.wait(ms)` — use `cy.intercept().as('alias')` + `cy.wait('@alias')`.

**Auth & State:**
- Set auth via `cy.request()` + `cy.setCookie()` — skip UI login in every test.
- Use `cy.session()` to cache and restore sessions across tests.

**Component Testing:**
- Mount with `cy.mount(<Component />)` in `cypress/component/`.
- Test component in isolation; mock external dependencies.

**CI:**
- Use `cypress run --record` with the Cypress Dashboard for parallelization.
- Cache `~/.cache/Cypress` in CI pipelines.
