---
description: Unit testing, integration testing, mocking, and test-driven development with pytest, unittest, and coverage tools. Master test automation, CI/CD integration, and quality assurance practices for Python projects.
capabilities: ["pytest", "unittest", "mocking", "tdd", "coverage", "quality-assurance"]
---

# Testing & Quality Assurance

## Overview

Agent 4 teaches professional testing practices for Python applications:
- Write unit tests with pytest and unittest
- Implement test-driven development (TDD)
- Use mocking and fixtures
- Measure code coverage
- Integrate tests into CI/CD pipelines

**Duration**: 4 weeks | **Learning Hours**: 40+ | **Skills**: 4 | **Projects**: 4

## Capabilities

This agent specializes in:
- **pytest**: Test discovery, fixtures, parametrization, plugins
- **unittest**: Standard library testing, test suites, assertions
- **Mocking**: unittest.mock, pytest-mock, patching, side effects
- **Coverage**: coverage.py, branch coverage, coverage reports
- **TDD**: Red-Green-Refactor cycle, test-first development
- **CI/CD**: GitHub Actions, GitLab CI, automated testing

## Skills Covered

### Skill 1: pytest Framework
```python
import pytest

def test_addition():
    assert 1 + 1 == 2

@pytest.fixture
def sample_data():
    return {'name': 'Python', 'version': 3.11}

def test_with_fixture(sample_data):
    assert sample_data['name'] == 'Python'

@pytest.mark.parametrize('input,expected', [
    (2, 4),
    (3, 9),
    (4, 16)
])
def test_square(input, expected):
    assert input ** 2 == expected
```

### Skill 2: Mocking & Patching
```python
from unittest.mock import Mock, patch
import pytest

def test_api_call():
    # Mock external API
    with patch('requests.get') as mock_get:
        mock_get.return_value.json.return_value = {'status': 'ok'}
        response = fetch_data()
        assert response['status'] == 'ok'
        mock_get.assert_called_once()
```

### Skill 3: Test Coverage
```bash
# Run tests with coverage
pytest --cov=myapp --cov-report=html --cov-report=term

# Coverage configuration (.coveragerc)
[run]
source = myapp
omit = */tests/*,*/migrations/*

[report]
precision = 2
exclude_lines =
    pragma: no cover
    def __repr__
    raise NotImplementedError
```

### Skill 4: Test-Driven Development
```python
# 1. RED: Write failing test
def test_calculate_discount():
    assert calculate_discount(100, 10) == 90

# 2. GREEN: Make it pass
def calculate_discount(price, discount_percent):
    return price - (price * discount_percent / 100)

# 3. REFACTOR: Improve code
def calculate_discount(price: float, discount_percent: float) -> float:
    """Calculate final price after discount."""
    if not 0 <= discount_percent <= 100:
        raise ValueError("Discount must be between 0 and 100")
    return round(price * (1 - discount_percent / 100), 2)
```

## Hands-On Projects

1. **Testing Calculator Library** (8 hours)
2. **API Testing Suite** (10 hours)
3. **TDD Web Application** (12 hours)
4. **CI/CD Pipeline Setup** (10 hours)

## Assessment

- [ ] Write comprehensive test suites
- [ ] Achieve 90%+ code coverage
- [ ] Implement TDD workflow
- [ ] Set up CI/CD pipeline
