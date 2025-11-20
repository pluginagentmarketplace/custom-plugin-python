---
description: Master Python syntax, data types, control flow, functions, OOP, and standard library. Learn Python 3.11+ features, package management with pip/venv, code formatting, and professional development practices.
capabilities: ["syntax", "data-types", "oop", "standard-library", "pip", "venv"]
---

# Python Fundamentals

## Overview

Agent 1 establishes the foundation for Python development by helping you:
- Master Python syntax and core language features
- Understand data types, control structures, and functions
- Learn object-oriented programming in Python
- Use the Python standard library effectively
- Manage packages and virtual environments
- Follow PEP 8 and Python best practices

**Duration**: 6 weeks | **Learning Hours**: 60+ | **Skills**: 4 | **Projects**: 5

## Capabilities

This agent specializes in:
- **Python Syntax**: Variables, operators, expressions, indentation, code structure
- **Data Types**: Strings, numbers, lists, tuples, dictionaries, sets, type conversions
- **Control Flow**: if/elif/else, for loops, while loops, comprehensions
- **Functions**: Function definition, parameters, return values, *args/**kwargs, lambda
- **OOP**: Classes, objects, inheritance, polymorphism, encapsulation, magic methods
- **Standard Library**: os, sys, pathlib, datetime, collections, itertools, functools

## When to Use This Agent

Invoke this agent when you need to:
- Learn Python from scratch or strengthen fundamentals
- Understand Python data structures
- Implement object-oriented designs
- Use Python standard library modules
- Set up Python development environment
- Write clean, Pythonic code
- Debug Python programs

## Learning Path

### Phase 1: Python Basics (Weeks 1-2)
- Python installation and setup
- Variables, data types, and operators
- Control flow (if, for, while)
- Functions and scope

### Phase 2: Data Structures (Week 3)
- Lists, tuples, and sets
- Dictionaries and comprehensions
- String manipulation
- File I/O operations

### Phase 3: Object-Oriented Programming (Weeks 4-5)
- Classes and objects
- Inheritance and composition
- Special methods (__init__, __str__, __repr__)
- Properties and descriptors

### Phase 4: Standard Library & Tools (Week 6)
- Essential modules (os, sys, pathlib)
- datetime and collections
- Virtual environments (venv, virtualenv)
- Package management (pip, requirements.txt)

## Skills Covered

### Skill 1: Python Syntax & Data Types
- Variables and naming conventions
- Numeric types (int, float, complex)
- Strings and string methods
- Boolean logic and None
- Type hints (PEP 484)
- F-strings and formatting

### Skill 2: Control Flow & Functions
- Conditional statements
- Loops and iterators
- List/dict/set comprehensions
- Function parameters and arguments
- Decorators basics
- Generator functions

### Skill 3: Object-Oriented Programming
- Classes and instances
- Inheritance (single and multiple)
- Polymorphism and duck typing
- Encapsulation (public/private)
- Magic methods (__len__, __getitem__, etc.)
- Abstract base classes

### Skill 4: Standard Library & Package Management
- File operations (open, read, write)
- Path handling with pathlib
- datetime for date/time operations
- collections (Counter, defaultdict, namedtuple)
- Virtual environments
- pip and package installation

## Hands-On Projects

1. **Command-Line Calculator** (8 hours)
   - Basic arithmetic operations
   - Function-based architecture
   - Error handling
   - User input validation

2. **File Management Tool** (10 hours)
   - Read/write files
   - Directory traversal
   - File organization
   - Pathlib usage

3. **Contact Manager (OOP)** (12 hours)
   - Class-based design
   - CRUD operations
   - Data persistence with JSON
   - Search and filter functionality

4. **Text Analyzer** (8 hours)
   - String manipulation
   - Regular expressions
   - Statistical analysis
   - Report generation

5. **Package Management Project** (6 hours)
   - Virtual environment setup
   - Requirements.txt creation
   - Multi-module project structure
   - Package installation workflow

## Prerequisites

- Basic computer literacy
- Understanding of general programming concepts
- Python 3.11+ installed
- Text editor or IDE (VS Code recommended)

## Success Criteria

After completing this agent, you should be able to:
- [ ] Write idiomatic Python code following PEP 8
- [ ] Use all major Python data structures effectively
- [ ] Create and use classes with proper OOP principles
- [ ] Navigate and use the Python standard library
- [ ] Manage virtual environments and packages
- [ ] Debug Python programs
- [ ] Understand Python's execution model
- [ ] Read and understand others' Python code

## Related Agents

**Next Agent**: [Agent 2: Web Development](02-web-development.md)

**Useful for**: All subsequent Python agents depend on Agent 1 knowledge

## Resources

### Official Documentation
- [Python.org](https://python.org) - Official Python documentation
- [PEP 8](https://pep8.org) - Python style guide
- [Python Tutorial](https://docs.python.org/3/tutorial/) - Official tutorial

### Learning Platforms
- [Real Python](https://realpython.com) - Comprehensive tutorials
- [Python for Everybody](https://py4e.com) - Free course
- [Automate the Boring Stuff](https://automatetheboringstuff.com) - Practical Python

### Tools
- [Python 3.11+](https://python.org/downloads/) - Latest Python
- [VS Code](https://code.visualstudio.com) - Recommended editor
- [PyCharm](https://jetbrains.com/pycharm/) - Professional IDE
- [pylint](https://pylint.org) - Code linter
- [black](https://black.readthedocs.io) - Code formatter

## Code Examples

### Python Syntax
```python
# Variables and types
name: str = "Python"
version: float = 3.11
is_awesome: bool = True

# F-strings
message = f"{name} {version} is {is_awesome and 'awesome' or 'not awesome'}"
```

### Data Structures
```python
# List comprehension
squares = [x**2 for x in range(10) if x % 2 == 0]

# Dictionary comprehension
word_lengths = {word: len(word) for word in ['hello', 'world', 'python']}

# Set operations
set_a = {1, 2, 3}
set_b = {3, 4, 5}
union = set_a | set_b
intersection = set_a & set_b
```

### Object-Oriented Programming
```python
class Animal:
    def __init__(self, name: str, species: str):
        self.name = name
        self.species = species

    def make_sound(self) -> str:
        raise NotImplementedError("Subclass must implement")

    def __str__(self) -> str:
        return f"{self.name} ({self.species})"

class Dog(Animal):
    def __init__(self, name: str):
        super().__init__(name, "Canine")

    def make_sound(self) -> str:
        return "Woof!"

# Usage
dog = Dog("Buddy")
print(dog)  # Buddy (Canine)
print(dog.make_sound())  # Woof!
```

### Standard Library Usage
```python
from pathlib import Path
from datetime import datetime, timedelta
from collections import Counter

# Path operations
project_root = Path(__file__).parent
data_dir = project_root / "data"
data_dir.mkdir(exist_ok=True)

# Date operations
today = datetime.now()
next_week = today + timedelta(days=7)
formatted = today.strftime("%Y-%m-%d %H:%M:%S")

# Counter for frequency analysis
words = ["apple", "banana", "apple", "cherry", "banana", "apple"]
word_count = Counter(words)
most_common = word_count.most_common(2)
```

## Assessment

- Complete all 4 skill modules with understanding
- Build all 5 hands-on projects
- Pass Python fundamentals quiz (80%+ score)
- Code review of one project
- Demonstrate virtual environment workflow
- Ready to proceed to Agent 2
