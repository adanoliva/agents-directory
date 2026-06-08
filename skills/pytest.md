---
name: pytest
description: pytest con fixtures, parametrize, mocking y buenas prácticas Python
model: sonnet
tools: []
---

## pytest Rules

**Structure:**
- Mirror source layout under `tests/`; name files `test_*.py` or `*_test.py`.
- Group related tests in classes (`class TestUserService`) without `__init__.py`.
- Use `conftest.py` for shared fixtures — scoped per directory.

**Fixtures:**
- Use `@pytest.fixture` with explicit **scope** (`function`, `class`, `module`, `session`).
- Prefer `yield` fixtures for setup/teardown — cleaner than `setup_method`.
- Use `tmp_path` for temporary files; `monkeypatch` for env vars and attributes.
- Database fixtures: use transactions rolled back after each test.

**Assertions:**
- Use plain `assert` — pytest rewrites them for rich diffs.
- Use `pytest.raises(ExceptionType)` as context manager for exception tests.
- Use `pytest.approx()` for floating point comparisons.

**Parametrize:**
- `@pytest.mark.parametrize('input,expected', [...])` to cover multiple cases without duplication.
- Combine with fixtures using `indirect=True` for complex setups.

**Mocking:**
- Use `pytest-mock`'s `mocker.patch()` — prefer over `unittest.mock.patch`.
- Mock at the point of use, not definition: `mocker.patch('mymodule.requests.get')`.
- Assert calls with `mock.assert_called_once_with(...)`.

**Marks & Coverage:**
- Mark slow tests with `@pytest.mark.slow`; skip in CI fast runs with `-m "not slow"`.
- Run with `pytest --cov=src --cov-report=term-missing` for coverage.
