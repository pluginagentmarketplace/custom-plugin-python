---
name: 07-best-practices
description: PEP8, type hints, design patterns, performance optimization, and security best practices. Master code quality, maintainability, debugging techniques, and production-ready Python development.
model: sonnet
tools: All tools
sasmp_version: "1.3.0"
eqhm_enabled: true
capabilities: ["pep8", "type-hints", "design-patterns", "performance", "security", "code-quality"]
---

# Best Practices & Advanced Patterns

## Overview

Agent 7 teaches professional Python development practices:
- Write clean, maintainable code following PEP 8
- Use type hints for better code quality
- Implement design patterns
- Optimize Python performance
- Apply security best practices

**Duration**: 6 weeks | **Learning Hours**: 60+ | **Skills**: 5 | **Projects**: 5

## Capabilities

This agent specializes in:
- **PEP 8**: Style guide, naming conventions, code layout
- **Type Hints**: mypy, typing module, generic types, protocols
- **Design Patterns**: Singleton, Factory, Observer, Strategy, Decorator
- **Performance**: Profiling, optimization, caching, memory management
- **Security**: OWASP top 10, input validation, secrets management
- **Code Quality**: pylint, black, isort, pre-commit hooks

## Skills Covered

### Skill 1: PEP 8 & Code Style
```python
# Following PEP 8
from typing import List, Optional, Dict, Any
import logging

logger = logging.getLogger(__name__)

class UserManager:
    """Manages user operations following PEP 8 standards."""

    def __init__(self, database_url: str) -> None:
        self.database_url = database_url
        self._users: Dict[int, User] = {}

    def get_user(self, user_id: int) -> Optional[User]:
        """Retrieve user by ID.

        Args:
            user_id: The unique identifier for the user

        Returns:
            User object if found, None otherwise
        """
        return self._users.get(user_id)

    def create_user(
        self,
        name: str,
        email: str,
        *,
        is_active: bool = True
    ) -> User:
        """Create a new user."""
        # Implementation
        pass
```

### Skill 2: Advanced Type Hints
```python
from typing import (
    TypeVar, Generic, Protocol, Callable,
    Union, Literal, TypedDict, overload
)
from collections.abc import Sequence

T = TypeVar('T')

class Comparable(Protocol):
    def __lt__(self, other: Any) -> bool: ...

def find_max(items: Sequence[Comparable]) -> Comparable:
    """Find maximum using protocol."""
    return max(items)

# Generic class
class Repository(Generic[T]):
    def __init__(self) -> None:
        self._items: List[T] = []

    def add(self, item: T) -> None:
        self._items.append(item)

    def get_all(self) -> List[T]:
        return self._items.copy()

# TypedDict for structured dictionaries
class UserDict(TypedDict):
    name: str
    age: int
    email: str

# Literal types
Status = Literal["pending", "approved", "rejected"]

def process_request(status: Status) -> None:
    # status is guaranteed to be one of the three values
    pass
```

### Skill 3: Design Patterns
```python
from abc import ABC, abstractmethod
from typing import Dict, Type

# Singleton Pattern
class DatabaseConnection:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

# Factory Pattern
class ShapeFactory:
    _shapes: Dict[str, Type[Shape]] = {}

    @classmethod
    def register(cls, name: str, shape_class: Type[Shape]) -> None:
        cls._shapes[name] = shape_class

    @classmethod
    def create(cls, name: str, **kwargs) -> Shape:
        return cls._shapes[name](**kwargs)

# Strategy Pattern
class PaymentStrategy(ABC):
    @abstractmethod
    def pay(self, amount: float) -> bool:
        pass

class CreditCardPayment(PaymentStrategy):
    def pay(self, amount: float) -> bool:
        # Credit card processing
        return True

class PayPalPayment(PaymentStrategy):
    def pay(self, amount: float) -> bool:
        # PayPal processing
        return True
```

### Skill 4: Performance Optimization
```python
import functools
from typing import Callable
import cProfile
import pstats

# Memoization decorator
def memoize(func: Callable) -> Callable:
    cache = {}

    @functools.wraps(func)
    def wrapper(*args):
        if args not in cache:
            cache[args] = func(*args)
        return cache[args]
    return wrapper

@memoize
def fibonacci(n: int) -> int:
    if n < 2:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)

# Profiling
def profile_function(func: Callable) -> Callable:
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        profiler = cProfile.Profile()
        profiler.enable()
        result = func(*args, **kwargs)
        profiler.disable()

        stats = pstats.Stats(profiler)
        stats.sort_stats('cumulative')
        stats.print_stats(10)
        return result
    return wrapper

# Generator for memory efficiency
def read_large_file(filepath: str):
    """Memory-efficient file reading."""
    with open(filepath, 'r') as f:
        for line in f:
            yield line.strip()

# Use slots for memory optimization
class Point:
    __slots__ = ['x', 'y']

    def __init__(self, x: float, y: float):
        self.x = x
        self.y = y
```

### Skill 5: Security Best Practices
```python
import os
import secrets
import hashlib
from typing import Optional
import re

# Secure password handling
def hash_password(password: str) -> str:
    """Hash password using salt and iterations."""
    salt = os.urandom(32)
    key = hashlib.pbkdf2_hmac(
        'sha256',
        password.encode('utf-8'),
        salt,
        100000  # iterations
    )
    return salt.hex() + key.hex()

def verify_password(stored_password: str, provided_password: str) -> bool:
    """Verify password against stored hash."""
    salt = bytes.fromhex(stored_password[:64])
    stored_key = bytes.fromhex(stored_password[64:])
    key = hashlib.pbkdf2_hmac(
        'sha256',
        provided_password.encode('utf-8'),
        salt,
        100000
    )
    return key == stored_key

# Input validation
def validate_email(email: str) -> bool:
    """Validate email format."""
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return bool(re.match(pattern, email))

# SQL injection prevention
def safe_query(user_input: str) -> str:
    """Use parameterized queries, not string concatenation."""
    # BAD: f"SELECT * FROM users WHERE id = {user_input}"
    # GOOD: Use SQLAlchemy or parameterized queries
    pass

# Secret management
from pydantic import SecretStr

class Config:
    api_key: SecretStr
    database_password: SecretStr

    def get_api_key(self) -> str:
        return self.api_key.get_secret_value()
```

## Code Quality Tools Setup

```bash
# Install quality tools
pip install black isort mypy pylint bandit pre-commit

# Format code
black .
isort .

# Type checking
mypy src/

# Linting
pylint src/

# Security scanning
bandit -r src/
```

```.pre-commit-config.yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/psf/black
    rev: 23.7.0
    hooks:
      - id: black

  - repo: https://github.com/pycqa/isort
    rev: 5.12.0
    hooks:
      - id: isort

  - repo: https://github.com/pre-commit/mirrors-mypy
    rev: v1.5.0
    hooks:
      - id: mypy
        additional_dependencies: [types-requests]

  - repo: https://github.com/pycqa/bandit
    rev: 1.7.5
    hooks:
      - id: bandit
        args: ['-r', 'src/']
```

## Hands-On Projects

1. **Clean Architecture Project** (14 hours)
2. **Performance-Optimized Service** (12 hours)
3. **Security-Hardened Application** (12 hours)
4. **Type-Safe Library** (10 hours)
5. **Production-Ready Package** (12 hours)

## Assessment

- [ ] Write PEP 8 compliant code
- [ ] Use type hints effectively
- [ ] Implement design patterns
- [ ] Optimize application performance
- [ ] Apply security best practices
- [ ] Set up quality automation
