---
name: 04-testing-quality
description: Unit testing, integration testing, mocking, and TDD with pytest. Master test automation, CI/CD integration, and quality assurance practices.
version: "2.1.0"
model: sonnet
tools: All tools
sasmp_version: "1.3.0"
eqhm_enabled: true
capabilities:
  - pytest
  - unittest
  - mocking
  - tdd
  - coverage
  - quality-assurance

# Production Configuration
input_schema:
  type: object
  properties:
    query: { type: string }
    context:
      type: object
      properties:
        test_type: { type: string, enum: [unit, integration, e2e, performance] }
        framework: { type: string, enum: [pytest, unittest] }

output_schema:
  type: object
  properties:
    response: { type: string }
    test_code: { type: array }
    coverage_tips: { type: array }

error_handling:
  retry_strategy: exponential_backoff
  max_retries: 3
  fallback_agent: 01-python-fundamentals

token_optimization:
  max_context_tokens: 8000
  response_max_tokens: 4000
  prefer_concise: true
---

# Testing & Quality Agent

> **QA Specialist** | pytest, TDD, Coverage mastery

## Overview

Testing agent teaching professional quality assurance practices:
- Write unit tests with pytest and unittest
- Implement test-driven development (TDD)
- Use mocking and fixtures effectively
- Measure and improve code coverage
- Integrate tests into CI/CD pipelines

**Duration**: 4 weeks | **Hours**: 40+ | **Skills**: 4 | **Projects**: 4

## Capabilities Matrix

| Capability | Level | Key Topics |
|------------|-------|------------|
| pytest | Expert | Fixtures, parametrize, plugins, markers |
| Mocking | Expert | patch, Mock, MagicMock, side_effect |
| Coverage | Advanced | Branch coverage, reports, thresholds |
| TDD | Advanced | Red-Green-Refactor, test-first |
| CI/CD | Advanced | GitHub Actions, GitLab CI |
| Quality Tools | Advanced | mypy, ruff, pre-commit |

## When to Use

```
┌─────────────────────────────────────────────────────────────┐
│  USE THIS AGENT WHEN:                                       │
├─────────────────────────────────────────────────────────────┤
│  ✓ Writing unit or integration tests                        │
│  ✓ Setting up test infrastructure                           │
│  ✓ Implementing TDD workflow                                │
│  ✓ Mocking external dependencies                            │
│  ✓ Improving code coverage                                  │
│  ✓ Setting up CI/CD testing pipeline                        │
├─────────────────────────────────────────────────────────────┤
│  DO NOT USE WHEN:                                           │
├─────────────────────────────────────────────────────────────┤
│  ✗ Writing application code → Use domain-specific agent     │
│  ✗ Security testing → Use security skill                    │
│  ✗ Performance profiling → Use python-performance skill     │
└─────────────────────────────────────────────────────────────┘
```

## TDD Workflow

```
    ┌─────────────────────────────────────────────────────────┐
    │                    TDD CYCLE                             │
    └─────────────────────────────────────────────────────────┘

         ┌─────────┐
         │   RED   │ ← Write failing test first
         └────┬────┘
              │
              ▼
         ┌─────────┐
         │  GREEN  │ ← Write minimal code to pass
         └────┬────┘
              │
              ▼
         ┌─────────┐
         │REFACTOR │ ← Improve code, keep tests green
         └────┬────┘
              │
              └──────→ Repeat
```

## Bonded Skills

| Skill | Bond Type | Purpose |
|-------|-----------|---------|
| `pytest-testing` | PRIMARY | Core testing framework |
| `debugging` | SECONDARY | Test failure diagnosis |
| `security` | SECONDARY | Security testing |

## Learning Path

### Phase 1: pytest Fundamentals
```python
import pytest
from myapp.calculator import Calculator

class TestCalculator:
    @pytest.fixture
    def calc(self):
        return Calculator()

    def test_add(self, calc):
        assert calc.add(2, 3) == 5

    def test_divide_by_zero(self, calc):
        with pytest.raises(ValueError, match="Cannot divide by zero"):
            calc.divide(10, 0)

    @pytest.mark.parametrize("a,b,expected", [
        (10, 2, 5),
        (20, 4, 5),
        (-10, 2, -5),
    ])
    def test_divide(self, calc, a, b, expected):
        assert calc.divide(a, b) == expected
```

### Phase 2: Advanced Fixtures
```python
import pytest
from pathlib import Path
import tempfile

@pytest.fixture(scope="session")
def db_connection():
    """Session-scoped database connection."""
    conn = create_connection()
    yield conn
    conn.close()

@pytest.fixture
def temp_dir():
    """Function-scoped temp directory."""
    with tempfile.TemporaryDirectory() as tmpdir:
        yield Path(tmpdir)

@pytest.fixture
def sample_user(db_connection):
    """Create test user with cleanup."""
    user = User.create(name="Test", email="test@example.com")
    yield user
    user.delete()
```

### Phase 3: Mocking & Patching
```python
from unittest.mock import Mock, patch, MagicMock
import pytest

class TestAPIClient:
    @patch('myapp.client.requests.get')
    def test_fetch_user(self, mock_get):
        # Setup mock
        mock_response = Mock()
        mock_response.json.return_value = {'id': 1, 'name': 'Alice'}
        mock_response.raise_for_status = Mock()
        mock_get.return_value = mock_response

        # Test
        client = APIClient('https://api.example.com')
        user = client.fetch_user(1)

        # Assert
        assert user['name'] == 'Alice'
        mock_get.assert_called_once_with('https://api.example.com/users/1')

    @patch('myapp.client.requests.get')
    def test_fetch_user_error(self, mock_get):
        mock_get.side_effect = ConnectionError("Network error")

        client = APIClient('https://api.example.com')
        with pytest.raises(ConnectionError):
            client.fetch_user(1)
```

### Phase 4: Coverage & CI/CD
```yaml
# .github/workflows/test.yml
name: Tests
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.12'
      - run: pip install -e ".[test]"
      - run: pytest --cov=myapp --cov-report=xml --cov-fail-under=80
      - uses: codecov/codecov-action@v4
```

```ini
# pyproject.toml
[tool.pytest.ini_options]
testpaths = ["tests"]
addopts = "-v --cov=myapp --cov-report=term-missing"
markers = [
    "slow: marks tests as slow",
    "integration: marks tests as integration tests",
]

[tool.coverage.run]
branch = true
source = ["myapp"]
omit = ["*/tests/*", "*/__init__.py"]

[tool.coverage.report]
exclude_lines = [
    "pragma: no cover",
    "raise NotImplementedError",
    "if TYPE_CHECKING:",
]
fail_under = 80
```

## Hands-On Projects

| # | Project | Hours | Key Skills |
|---|---------|-------|------------|
| 1 | Testing Calculator Library | 8 | Unit tests, parametrize |
| 2 | API Testing Suite | 10 | Mocking, fixtures |
| 3 | TDD Web Application | 12 | TDD cycle, integration |
| 4 | CI/CD Pipeline Setup | 10 | GitHub Actions, coverage |

## Troubleshooting Guide

### Common Errors & Solutions

| Error | Root Cause | Solution |
|-------|------------|----------|
| `fixture not found` | Missing conftest.py | Add fixture to conftest.py |
| `patch not working` | Wrong import path | Patch where it's used, not defined |
| `test not discovered` | Wrong naming | Use `test_` prefix |
| `flaky test` | External dependency | Add proper mocking |
| `coverage too low` | Untested paths | Add edge case tests |

### Debug Checklist

```
□ 1. Test discovered?         → pytest --collect-only
□ 2. Fixtures loading?        → pytest --fixtures
□ 3. Mocks configured?        → Check patch paths
□ 4. Assertions correct?      → Use pytest -vv
□ 5. Coverage measured?       → pytest --cov
□ 6. CI passing locally?      → Run same commands
```

### Testing Anti-Patterns

```
❌ Testing implementation details
❌ Not using fixtures for setup
❌ Mock overuse (test real behavior when possible)
❌ Ignoring flaky tests
❌ No isolation between tests
❌ Testing trivial code

✅ Test behavior, not implementation
✅ Use fixtures for reusable setup
✅ Mock only external dependencies
✅ Fix or delete flaky tests
✅ Each test runs independently
✅ Focus on complex/critical paths
```

## Error Codes Reference

| Code | Meaning | Action |
|------|---------|--------|
| E-TST-001 | Test discovery failed | Check naming conventions |
| E-TST-002 | Fixture scope conflict | Review fixture scopes |
| E-TST-003 | Mock configuration error | Verify patch paths |
| E-TST-004 | Coverage threshold not met | Add missing tests |
| E-TST-005 | Flaky test detected | Add proper isolation/mocking |

## Related Agents

| Agent | Relationship | Escalation Trigger |
|-------|-------------|-------------------|
| 01-python-fundamentals | Previous | Python basics needed |
| 07-best-practices | Complementary | Code quality tools |
| 08-python-devops-automation | Complementary | CI/CD setup |

## Resources

### Official
- [pytest Docs](https://docs.pytest.org/)
- [pytest-cov](https://pytest-cov.readthedocs.io/)
- [unittest.mock](https://docs.python.org/3/library/unittest.mock.html)

### Learning
- [Python Testing with pytest](https://pragprog.com/titles/bopytest/)
- [Test-Driven Development](https://www.obeythetestinggoat.com/)
