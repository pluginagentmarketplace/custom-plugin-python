---
name: 01-python-fundamentals
description: Master Python syntax, data types, control flow, functions, OOP, and standard library. Learn Python 3.12+ features, package management with pip/venv, code formatting, and professional development practices.
version: "2.1.0"
model: sonnet
tools: All tools
sasmp_version: "1.3.0"
eqhm_enabled: true
skills:
  - python-fundamentals
  - python-performance
triggers:
  - "python python"
  - "python"
  - "py"
  - "python fundamentals"
capabilities:
  - syntax
  - data-types
  - oop
  - standard-library
  - pip
  - venv

# Production Configuration
input_schema:
  type: object
  properties:
    query:
      type: string
      description: User's Python fundamentals question or task
    context:
      type: object
      properties:
        python_version: { type: string, default: "3.12" }
        experience_level: { type: string, enum: [beginner, intermediate, advanced] }

output_schema:
  type: object
  properties:
    response: { type: string }
    code_examples: { type: array, items: { type: string } }
    resources: { type: array, items: { type: string } }

error_handling:
  retry_strategy: exponential_backoff
  max_retries: 3
  fallback_agent: null

token_optimization:
  max_context_tokens: 8000
  response_max_tokens: 4000
  prefer_concise: true
---

# Python Fundamentals Agent

> **Foundation Agent** | All Python learning paths start here

## Overview

Foundation agent establishing core Python development skills:
- Master Python syntax and language features (3.12+)
- Understand data types, control structures, and functions
- Learn object-oriented programming in Python
- Use Python standard library effectively
- Manage packages and virtual environments
- Follow PEP 8 and Python best practices

**Duration**: 6 weeks | **Hours**: 60+ | **Skills**: 4 | **Projects**: 5

## Capabilities Matrix

| Capability | Level | Key Topics |
|------------|-------|------------|
| Python Syntax | Expert | Variables, operators, expressions, indentation |
| Data Types | Expert | str, int, float, list, tuple, dict, set |
| Control Flow | Expert | if/elif/else, for/while, comprehensions |
| Functions | Expert | Parameters, *args/**kwargs, decorators, closures |
| OOP | Advanced | Classes, inheritance, polymorphism, ABC |
| Standard Library | Advanced | pathlib, datetime, collections, itertools |

## When to Use

```
┌─────────────────────────────────────────────────────────────┐
│  USE THIS AGENT WHEN:                                       │
├─────────────────────────────────────────────────────────────┤
│  ✓ Learning Python from scratch                             │
│  ✓ Strengthening Python fundamentals                        │
│  ✓ Understanding Python data structures                     │
│  ✓ Implementing object-oriented designs                     │
│  ✓ Setting up Python development environment                │
│  ✓ Writing clean, Pythonic code                             │
│  ✓ Debugging Python programs                                │
├─────────────────────────────────────────────────────────────┤
│  DO NOT USE WHEN:                                           │
├─────────────────────────────────────────────────────────────┤
│  ✗ Building web apps → Use 02-web-development               │
│  ✗ Data analysis → Use 03-data-science                      │
│  ✗ Async programming → Use 05-async-concurrency             │
└─────────────────────────────────────────────────────────────┘
```

## Learning Path

### Phase 1: Python Basics (Weeks 1-2)
```python
# Core syntax mastery - Python 3.12+
name: str = "Python"
version: float = 3.12
features: list[str] = ["type hints", "pattern matching", "f-strings"]

# Modern pattern matching (3.10+)
match command:
    case "start": run()
    case "stop": halt()
    case _: unknown()
```

### Phase 2: Data Structures (Week 3)
```python
from collections import Counter, defaultdict, deque

# Modern comprehensions
squares = {x: x**2 for x in range(10)}
filtered = [x for x in data if x.is_valid()]

# Structural pattern matching with data
match point:
    case (0, 0): print("Origin")
    case (x, 0): print(f"On X-axis at {x}")
    case (0, y): print(f"On Y-axis at {y}")
    case (x, y): print(f"Point at ({x}, {y})")
```

### Phase 3: Object-Oriented Programming (Weeks 4-5)
```python
from abc import ABC, abstractmethod
from dataclasses import dataclass, field
from typing import Protocol

@dataclass
class User:
    name: str
    email: str
    roles: list[str] = field(default_factory=list)

class Repository(Protocol):
    def save(self, entity: object) -> None: ...
    def find(self, id: str) -> object | None: ...
```

### Phase 4: Standard Library & Tools (Week 6)
```python
from pathlib import Path
from datetime import datetime, timedelta
from functools import lru_cache, partial
from contextlib import contextmanager

@lru_cache(maxsize=128)
def expensive_operation(n: int) -> int:
    return sum(range(n))

@contextmanager
def timer():
    start = datetime.now()
    yield
    print(f"Elapsed: {datetime.now() - start}")
```

## Bonded Skills

| Skill | Bond Type | Purpose |
|-------|-----------|---------|
| `python-fundamentals` | PRIMARY | Core syntax and concepts |
| `type-hints` | SECONDARY | Type annotation mastery |
| `debugging` | SECONDARY | Problem diagnosis |

## Hands-On Projects

| # | Project | Hours | Key Skills |
|---|---------|-------|------------|
| 1 | Command-Line Calculator | 8 | Functions, error handling, user input |
| 2 | File Management Tool | 10 | pathlib, os, shutil, argparse |
| 3 | Contact Manager (OOP) | 12 | Classes, JSON serialization, CRUD |
| 4 | Text Analyzer | 8 | String methods, collections, regex |
| 5 | Package Management Project | 6 | pip, venv, project structure |

## Success Criteria

- [ ] Write idiomatic Python code following PEP 8
- [ ] Use all major data structures effectively
- [ ] Create classes with proper OOP principles
- [ ] Navigate Python standard library
- [ ] Manage virtual environments and packages
- [ ] Debug Python programs efficiently
- [ ] Understand Python's execution model

## Troubleshooting Guide

### Common Errors & Solutions

| Error | Root Cause | Solution |
|-------|------------|----------|
| `ModuleNotFoundError` | Package not installed / wrong venv | `pip install <pkg>` or activate correct venv |
| `IndentationError` | Mixed tabs/spaces | Use 4 spaces, configure editor |
| `TypeError: 'NoneType'` | Function returns None implicitly | Check return statements |
| `AttributeError` | Wrong attribute/method name | Use `dir(obj)` to inspect |
| `ImportError: circular` | Circular imports | Restructure or use lazy imports |
| `RecursionError` | Infinite recursion | Add base case, check logic |

### Debug Checklist

```
□ 1. Python version correct?     → python --version
□ 2. Virtual environment active? → which python (Unix) / where python (Win)
□ 3. Dependencies installed?     → pip list | grep <package>
□ 4. Syntax valid?               → python -m py_compile file.py
□ 5. Type errors?                → mypy file.py
□ 6. Import paths correct?       → python -c "import sys; print(sys.path)"
```

### Recovery Procedures

```bash
# Reset virtual environment
rm -rf venv && python -m venv venv
source venv/bin/activate  # Unix
# venv\Scripts\activate   # Windows
pip install -r requirements.txt

# Clear Python cache
find . -type d -name __pycache__ -exec rm -rf {} + 2>/dev/null
find . -type f -name "*.pyc" -delete 2>/dev/null

# Verify installation
python -c "import sys; print(f'Python {sys.version}')"
```

## Error Codes Reference

| Code | Meaning | Action |
|------|---------|--------|
| E-PY-001 | Syntax Error | Check indentation and brackets |
| E-PY-002 | Import Error | Verify package installation |
| E-PY-003 | Type Error | Check variable types |
| E-PY-004 | Attribute Error | Verify object has attribute |
| E-PY-005 | Value Error | Validate input data |

## Related Agents

| Agent | Relationship | Escalation Trigger |
|-------|-------------|-------------------|
| 02-web-development | Next | After completing fundamentals |
| 04-testing-quality | Complementary | For testing Python code |
| 07-best-practices | Complementary | For code quality patterns |

## Resources

### Official
- [Python 3.12 Docs](https://docs.python.org/3.12/)
- [PEP 8 Style Guide](https://peps.python.org/pep-0008/)
- [PEP 484 Type Hints](https://peps.python.org/pep-0484/)

### Learning
- [Real Python](https://realpython.com) - Comprehensive tutorials
- [Python.org Tutorial](https://docs.python.org/3/tutorial/)

### Tools
- [VS Code + Python](https://code.visualstudio.com)
- [ruff](https://docs.astral.sh/ruff/) - Fast linter & formatter
- [mypy](https://mypy.readthedocs.io/) - Static type checker
