---
name: roadmap
description: Python developer learning roadmap and career paths
version: "2.1.0"
allowed-tools: Read
exit_codes:
  0: success
  1: invalid_path
---

# /roadmap

Start your Python developer journey with structured learning paths.

## Python Learning Paths

### Path 1: Python Fundamentals (6 weeks)
**Agent:** `01-python-fundamentals`

```
Week 1-2: Basics
├── Syntax, variables, data types
├── Control flow (if, for, while)
└── Functions and modules

Week 3-4: Data Structures
├── Lists, tuples, sets, dicts
├── Comprehensions
└── Iterators and generators

Week 5-6: OOP & Standard Library
├── Classes and inheritance
├── Magic methods
└── pathlib, datetime, collections
```

**Exit Criteria:** Build a CLI tool with proper OOP structure

---

### Path 2: Web Development (8 weeks)
**Agent:** `02-web-development`
**Prerequisite:** Python Fundamentals

```
Week 1-2: Flask Basics
├── Routes and views
├── Templates (Jinja2)
└── Forms and validation

Week 3-4: Django Framework
├── Models and ORM
├── Admin interface
└── Authentication

Week 5-6: FastAPI & Modern APIs
├── Pydantic models
├── Async endpoints
└── OpenAPI docs

Week 7-8: Production Deployment
├── Docker containerization
├── Database migrations
└── CI/CD setup
```

**Exit Criteria:** Deploy a full-stack web application

---

### Path 3: Data Science & ML (10 weeks)
**Agent:** `03-data-science`
**Prerequisite:** Python Fundamentals

```
Week 1-2: NumPy Foundations
├── Arrays and operations
├── Broadcasting
└── Linear algebra

Week 3-5: Pandas Mastery
├── DataFrames and Series
├── Data cleaning
├── GroupBy and aggregations
└── Time series

Week 6-7: Visualization
├── Matplotlib
├── Seaborn
└── Interactive plots

Week 8-10: Machine Learning Intro
├── scikit-learn basics
├── Classification & regression
└── Model evaluation
```

**Exit Criteria:** Complete data analysis project with ML model

---

### Path 4: Testing & Quality (4 weeks)
**Agent:** `04-testing-quality`
**Prerequisite:** Python Fundamentals

```
Week 1: pytest Fundamentals
├── Test discovery
├── Assertions
└── Markers and parametrize

Week 2: Fixtures & Mocking
├── Fixture scopes
├── unittest.mock
└── External dependencies

Week 3: TDD Practice
├── Red-Green-Refactor
├── Test-first development
└── Integration tests

Week 4: CI/CD & Coverage
├── GitHub Actions
├── Coverage reports
└── Pre-commit hooks
```

**Exit Criteria:** Achieve 90%+ coverage on a project

---

### Path 5: Async & Performance (6 weeks)
**Agent:** `05-async-concurrency`
**Prerequisite:** Python Fundamentals

```
Week 1-2: asyncio Basics
├── Coroutines and await
├── Event loop
└── Tasks and gather

Week 3-4: Advanced Async
├── aiohttp client/server
├── WebSockets
└── Task groups (3.11+)

Week 5-6: Concurrency Options
├── Threading for I/O
├── Multiprocessing for CPU
└── concurrent.futures
```

**Exit Criteria:** Build a high-performance async web scraper

---

### Path 6: Packaging & DevOps (4 weeks)
**Agent:** `06-package-deployment`, `08-python-devops-automation`
**Prerequisite:** Python Fundamentals

```
Week 1: Poetry & Project Structure
├── pyproject.toml
├── Dependency management
└── src layout

Week 2: Docker & Containers
├── Multi-stage builds
├── Docker Compose
└── Image optimization

Week 3: CI/CD Pipelines
├── GitHub Actions
├── Automated testing
└── Release automation

Week 4: Production Deployment
├── Cloud platforms
├── Monitoring
└── Secrets management
```

**Exit Criteria:** Publish a package to PyPI with full CI/CD

---

## Career Tracks

### Junior Python Developer
```
Required:
├── Python Fundamentals ✓
├── Basic Web Development ✓
└── Testing Basics ✓

Timeline: 3-6 months
```

### Mid-Level Python Developer
```
Required:
├── All Junior skills ✓
├── Advanced Web (Django/FastAPI) ✓
├── Database design ✓
├── Testing & CI/CD ✓
└── Docker basics ✓

Timeline: 1-2 years
```

### Senior Python Developer
```
Required:
├── All Mid-Level skills ✓
├── System design ✓
├── Performance optimization ✓
├── Security best practices ✓
├── Mentoring abilities ✓
└── Architecture decisions ✓

Timeline: 3-5 years
```

### Specialist Tracks

**Data Engineer:**
```
Focus: Path 1 → Path 3 → Async → DevOps
Skills: Pandas, Spark, Airflow, ETL
```

**Backend Engineer:**
```
Focus: Path 1 → Path 2 → Path 4 → Path 6
Skills: FastAPI, PostgreSQL, Redis, Docker
```

**ML Engineer:**
```
Focus: Path 1 → Path 3 → Advanced ML → MLOps
Skills: PyTorch, MLflow, Kubernetes
```

---

## Next Steps

1. **Assess current level:** Use `/skill-assessment`
2. **Choose your path:** Based on career goals
3. **Get agent guidance:** Use `/agent-guide`
4. **Build projects:** Use `/project-builder`
5. **Track progress:** Complete exit criteria
