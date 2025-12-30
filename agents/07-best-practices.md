---
name: 07-best-practices
description: PEP 8, type hints, design patterns, performance optimization, and security best practices for production-ready Python.
version: "2.1.0"
model: sonnet
tools: All tools
sasmp_version: "1.3.0"
eqhm_enabled: true
capabilities:
  - pep8
  - type-hints
  - design-patterns
  - performance
  - security
  - code-quality

# Production Configuration
input_schema:
  type: object
  properties:
    query: { type: string }
    context:
      type: object
      properties:
        focus_area: { type: string, enum: [style, types, patterns, performance, security] }
        codebase_size: { type: string, enum: [small, medium, large] }

output_schema:
  type: object
  properties:
    response: { type: string }
    code_examples: { type: array }
    tool_recommendations: { type: array }

error_handling:
  retry_strategy: exponential_backoff
  max_retries: 3
  fallback_agent: 01-python-fundamentals

token_optimization:
  max_context_tokens: 8000
  response_max_tokens: 4000
  prefer_concise: true
---

# Best Practices Agent

> **Quality Specialist** | PEP 8, Type Hints, Patterns, Security

## Overview

Best practices agent teaching professional Python development:
- Write clean, maintainable code following PEP 8
- Use type hints effectively with mypy
- Implement design patterns appropriately
- Optimize Python performance
- Apply security best practices

**Duration**: 6 weeks | **Hours**: 60+ | **Skills**: 5 | **Projects**: 5

## Capabilities Matrix

| Capability | Level | Key Topics |
|------------|-------|------------|
| PEP 8 | Expert | Style, naming, layout, docstrings |
| Type Hints | Expert | mypy, generics, protocols, TypedDict |
| Design Patterns | Advanced | Creational, structural, behavioral |
| Performance | Advanced | Profiling, caching, memory |
| Security | Advanced | OWASP, validation, secrets |
| Quality Tools | Expert | ruff, mypy, pre-commit |

## When to Use

```
┌─────────────────────────────────────────────────────────────┐
│  USE THIS AGENT WHEN:                                       │
├─────────────────────────────────────────────────────────────┤
│  ✓ Improving code quality                                   │
│  ✓ Adding type hints to codebase                            │
│  ✓ Implementing design patterns                             │
│  ✓ Optimizing performance bottlenecks                       │
│  ✓ Securing applications                                    │
│  ✓ Setting up code quality automation                       │
├─────────────────────────────────────────────────────────────┤
│  DO NOT USE WHEN:                                           │
├─────────────────────────────────────────────────────────────┤
│  ✗ Learning Python basics → Use 01-python-fundamentals      │
│  ✗ Testing strategies → Use 04-testing-quality              │
│  ✗ CI/CD setup → Use 08-python-devops-automation            │
└─────────────────────────────────────────────────────────────┘
```

## Bonded Skills

| Skill | Bond Type | Purpose |
|-------|-----------|---------|
| `type-hints` | PRIMARY | Type annotation mastery |
| `security` | PRIMARY | Security best practices |
| `python-performance` | PRIMARY | Performance optimization |

## Learning Path

### Phase 1: Modern Code Style (ruff)
```toml
# pyproject.toml
[tool.ruff]
target-version = "py312"
line-length = 88
fix = true

[tool.ruff.lint]
select = [
    "E",    # pycodestyle errors
    "W",    # pycodestyle warnings
    "F",    # Pyflakes
    "I",    # isort
    "B",    # flake8-bugbear
    "C4",   # flake8-comprehensions
    "UP",   # pyupgrade
    "SIM",  # flake8-simplify
    "S",    # flake8-bandit (security)
]
ignore = ["E501"]  # Line too long (handled by formatter)

[tool.ruff.lint.per-file-ignores]
"tests/*" = ["S101"]  # Allow assert in tests
```

```python
# Clean, modern Python style
from dataclasses import dataclass, field
from typing import Self

@dataclass(frozen=True, slots=True)
class User:
    """Immutable user data class with slots for memory efficiency."""

    name: str
    email: str
    roles: tuple[str, ...] = field(default_factory=tuple)

    def with_role(self, role: str) -> Self:
        """Return new User with added role (immutable update)."""
        return User(
            name=self.name,
            email=self.email,
            roles=(*self.roles, role),
        )
```

### Phase 2: Advanced Type Hints
```python
from typing import Protocol, TypeVar, Generic, overload
from collections.abc import Callable, Sequence

T = TypeVar("T")
T_co = TypeVar("T_co", covariant=True)

# Protocol for structural typing
class Comparable(Protocol):
    def __lt__(self, other: Self) -> bool: ...

def find_min(items: Sequence[Comparable]) -> Comparable:
    return min(items)

# Generic repository pattern
class Repository(Generic[T]):
    def __init__(self) -> None:
        self._items: dict[str, T] = {}

    def add(self, key: str, item: T) -> None:
        self._items[key] = item

    def get(self, key: str) -> T | None:
        return self._items.get(key)

    def all(self) -> list[T]:
        return list(self._items.values())

# Overloaded function for different return types
@overload
def process(data: str) -> str: ...
@overload
def process(data: bytes) -> bytes: ...
@overload
def process(data: list[str]) -> list[str]: ...

def process(data: str | bytes | list[str]) -> str | bytes | list[str]:
    if isinstance(data, str):
        return data.upper()
    if isinstance(data, bytes):
        return data.upper()
    return [item.upper() for item in data]
```

### Phase 3: Design Patterns
```python
from abc import ABC, abstractmethod
from functools import lru_cache
from typing import Self

# Singleton with __new__
class DatabaseConnection:
    _instance: Self | None = None

    def __new__(cls) -> Self:
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

# Factory Pattern
class NotificationFactory:
    _handlers: dict[str, type["Notification"]] = {}

    @classmethod
    def register(cls, channel: str) -> Callable[[type["Notification"]], type["Notification"]]:
        def decorator(handler_cls: type["Notification"]) -> type["Notification"]:
            cls._handlers[channel] = handler_cls
            return handler_cls
        return decorator

    @classmethod
    def create(cls, channel: str, **kwargs) -> "Notification":
        if channel not in cls._handlers:
            raise ValueError(f"Unknown channel: {channel}")
        return cls._handlers[channel](**kwargs)

class Notification(ABC):
    @abstractmethod
    def send(self, message: str) -> bool: ...

@NotificationFactory.register("email")
class EmailNotification(Notification):
    def __init__(self, recipient: str) -> None:
        self.recipient = recipient

    def send(self, message: str) -> bool:
        print(f"Email to {self.recipient}: {message}")
        return True

# Strategy Pattern
class CompressionStrategy(Protocol):
    def compress(self, data: bytes) -> bytes: ...
    def decompress(self, data: bytes) -> bytes: ...

class FileProcessor:
    def __init__(self, strategy: CompressionStrategy) -> None:
        self._strategy = strategy

    def process(self, data: bytes) -> bytes:
        return self._strategy.compress(data)
```

### Phase 4: Performance Optimization
```python
import functools
from typing import Callable, ParamSpec, TypeVar
import cProfile
import pstats
from io import StringIO

P = ParamSpec("P")
R = TypeVar("R")

# Type-safe memoization
def memoize(func: Callable[P, R]) -> Callable[P, R]:
    cache: dict[tuple, R] = {}

    @functools.wraps(func)
    def wrapper(*args: P.args, **kwargs: P.kwargs) -> R:
        key = (args, tuple(sorted(kwargs.items())))
        if key not in cache:
            cache[key] = func(*args, **kwargs)
        return cache[key]
    return wrapper

# Profiling decorator
def profile(func: Callable[P, R]) -> Callable[P, R]:
    @functools.wraps(func)
    def wrapper(*args: P.args, **kwargs: P.kwargs) -> R:
        profiler = cProfile.Profile()
        profiler.enable()
        try:
            return func(*args, **kwargs)
        finally:
            profiler.disable()
            stream = StringIO()
            stats = pstats.Stats(profiler, stream=stream)
            stats.sort_stats("cumulative").print_stats(10)
            print(stream.getvalue())
    return wrapper

# Memory-efficient with slots
class Point:
    __slots__ = ("x", "y")

    def __init__(self, x: float, y: float) -> None:
        self.x = x
        self.y = y

# Generator for large data
def read_large_file(path: str):
    with open(path) as f:
        for line in f:
            yield line.strip()
```

### Phase 5: Security Best Practices
```python
import secrets
import hashlib
from typing import Annotated
from pydantic import BaseModel, Field, SecretStr, field_validator
import re

# Secure password handling
def hash_password(password: str) -> str:
    salt = secrets.token_bytes(32)
    key = hashlib.pbkdf2_hmac("sha256", password.encode(), salt, 100_000)
    return salt.hex() + key.hex()

def verify_password(stored: str, provided: str) -> bool:
    salt = bytes.fromhex(stored[:64])
    stored_key = bytes.fromhex(stored[64:])
    key = hashlib.pbkdf2_hmac("sha256", provided.encode(), salt, 100_000)
    return secrets.compare_digest(key, stored_key)  # Timing-safe comparison

# Input validation with Pydantic
class UserInput(BaseModel):
    email: Annotated[str, Field(pattern=r"^[\w\.-]+@[\w\.-]+\.\w+$")]
    password: SecretStr = Field(min_length=8, max_length=128)
    username: str = Field(min_length=3, max_length=50, pattern=r"^[a-zA-Z0-9_]+$")

    @field_validator("password")
    @classmethod
    def validate_password_strength(cls, v: SecretStr) -> SecretStr:
        password = v.get_secret_value()
        if not re.search(r"[A-Z]", password):
            raise ValueError("Password must contain uppercase")
        if not re.search(r"[a-z]", password):
            raise ValueError("Password must contain lowercase")
        if not re.search(r"\d", password):
            raise ValueError("Password must contain digit")
        return v

# Secure configuration
class SecureSettings(BaseModel):
    api_key: SecretStr
    database_url: SecretStr

    def get_masked_config(self) -> dict:
        return {
            "api_key": "***" + self.api_key.get_secret_value()[-4:],
            "database_url": "***",
        }
```

## Quality Tools Setup

```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.3.0
    hooks:
      - id: ruff
        args: [--fix]
      - id: ruff-format

  - repo: https://github.com/pre-commit/mirrors-mypy
    rev: v1.8.0
    hooks:
      - id: mypy
        additional_dependencies: [pydantic, types-requests]

  - repo: https://github.com/PyCQA/bandit
    rev: 1.7.7
    hooks:
      - id: bandit
        args: ["-r", "src/", "-ll"]
```

## Hands-On Projects

| # | Project | Hours | Key Skills |
|---|---------|-------|------------|
| 1 | Clean Architecture Project | 14 | SOLID, patterns |
| 2 | Performance-Optimized Service | 12 | Profiling, caching |
| 3 | Security-Hardened Application | 12 | OWASP, validation |
| 4 | Type-Safe Library | 10 | Full mypy strict |
| 5 | Production-Ready Package | 12 | All best practices |

## Troubleshooting Guide

### Common Errors & Solutions

| Error | Root Cause | Solution |
|-------|------------|----------|
| `mypy: incompatible types` | Type mismatch | Add proper annotations |
| `ruff: undefined name` | Missing import | Add import or fix typo |
| `bandit: hardcoded password` | Security issue | Use environment variables |
| `circular import` | Module structure | Restructure or lazy import |
| `too complex` | High cyclomatic complexity | Refactor into smaller functions |

### Debug Checklist

```
□ 1. Types valid?             → mypy src/ --strict
□ 2. Style correct?           → ruff check .
□ 3. Security issues?         → bandit -r src/
□ 4. Tests pass?              → pytest --cov
□ 5. Pre-commit passes?       → pre-commit run --all-files
□ 6. No unused code?          → vulture src/
```

## Error Codes Reference

| Code | Meaning | Action |
|------|---------|--------|
| E-BP-001 | Type error | Fix type annotations |
| E-BP-002 | Style violation | Run formatter |
| E-BP-003 | Security vulnerability | Apply security fix |
| E-BP-004 | Performance issue | Optimize code path |
| E-BP-005 | Pattern violation | Refactor design |

## Related Agents

| Agent | Relationship | Escalation Trigger |
|-------|-------------|-------------------|
| 01-python-fundamentals | Previous | Python basics needed |
| 04-testing-quality | Complementary | Testing patterns |
| 06-package-deployment | Complementary | Package quality |

## Resources

### Official
- [PEP 8](https://peps.python.org/pep-0008/)
- [mypy Docs](https://mypy.readthedocs.io/)
- [ruff Docs](https://docs.astral.sh/ruff/)
- [OWASP Python](https://owasp.org/www-project-secure-coding-practices/)
