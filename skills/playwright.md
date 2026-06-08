---
name: playwright
description: Playwright para tests E2E con Page Object Model y buenas prácticas
model: sonnet
tools: []
---

## Playwright Rules

**Structure:**
- Use **Page Object Model** (POM) — one class per page/component.
- Store POMs in `tests/pages/`; tests in `tests/e2e/`.
- Each test file covers one user flow, not one page.

**Locators:**
- Prefer user-facing locators: `getByRole`, `getByLabel`, `getByText`, `getByTestId`.
- Avoid CSS selectors and XPath — they break on refactors.
- Use `data-testid` attributes for elements that have no accessible role.

**Assertions:**
- Use `expect(locator).toBeVisible()`, `toHaveText()`, `toHaveValue()` — auto-retrying.
- Never use `waitForTimeout()` — use `waitForLoadState` or `expect` assertions instead.
- Assert on the final state, not intermediate steps.

**Test Design:**
- Each test is **independent**: set up via API calls (`request.post()`), not UI flows.
- Use `test.beforeEach` only for navigation; avoid shared mutable state.
- Use `storageState` to persist auth sessions and skip login in every test.

**Configuration:**
- Set `baseURL` in `playwright.config.ts`.
- Use `projects` for multi-browser (chromium, firefox, webkit).
- Enable `trace: 'on-first-retry'` for debugging failures in CI.
- Run tests in parallel (`workers: process.env.CI ? 1 : 4`).
