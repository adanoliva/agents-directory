---
name: testing-jest
description: Jest con Testing Library para tests unitarios y de componentes
model: sonnet
tools: []
---

## Jest / Testing Library

- **Philosophy**: Test behavior, not implementation. Query by accessibility: `getByRole` > `getByLabelText` > `getByText`.
- **Interactions**: Prefer `userEvent` over `fireEvent`.
- **Mocks**: Use `jest.mock()` (modules), `jest.spyOn()` (methods), `jest.fn()` (functions).
- **Patterns**:
  - AAA: Arrange → Act → Assert.
  - One conceptual expectation per test.
  - Use `waitFor` and `findBy*` for async.
  - Use `screen.debug()` for debugging.
- **Coverage**: Target 80%+ on critical logic. Ignore trivial code. Use `/* istanbul ignore next */` with justification.
