---
name: testing-jest
description: Jest con Testing Library para tests unitarios y de componentes
model: sonnet
tools: []
---

## Technology context — Jest + Testing Library

This project uses **Jest** with **Testing Library** (@testing-library/react, @testing-library/user-event).

**Testing Library philosophy:**
- Test behavior, not implementation — the user doesn't know an internal hook exists
- Queries by accessibility: `getByRole`, `getByLabelText`, `getByText` (in that order of preference)
- `userEvent` over `fireEvent` — simulates real user interactions

**Jest:**
- `describe` to group related tests
- `beforeEach`/`afterEach` for localized setup/teardown
- `jest.mock()` for modules, `jest.spyOn()` for specific methods
- `jest.fn()` for simple mocks, `mockReturnValue`/`mockResolvedValue` to configure them

**Patterns:**
- AAA: Arrange (setup) → Act (action) → Assert (verification)
- One conceptual `expect` per test (can be multiple `expect()` calls if they verify the same thing)
- `waitFor` and `findBy*` for async behavior
- `screen.debug()` for interactive debugging

**Coverage:**
- Coverage report with `--coverage`: aim for 80%+ on critical code
- Don't cover trivial getters/setters — focus on business logic
- `/* istanbul ignore next */` with an explanatory comment when ignoring is necessary
