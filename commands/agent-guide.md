---
name: agent-guide
description: Navigate Python developer agents and get expert guidance
version: "2.1.0"
allowed-tools: Read
exit_codes:
  0: success
  1: agent_not_found
  2: invalid_input
---

# /agent-guide

Get expert guidance from specialized Python development agents.

## Python Developer Agents

### 01 - Python Fundamentals Agent
**Expertise:** Core Python syntax, data types, OOP, standard library

**Use When:**
- Learning Python from scratch
- Understanding Python data structures
- Implementing OOP designs
- Setting up development environment

**Skills:** `python-fundamentals`, `type-hints`, `debugging`

---

### 02 - Web Development Agent
**Expertise:** Django, Flask, FastAPI, REST APIs, authentication

**Use When:**
- Building web applications
- Creating REST/GraphQL APIs
- Implementing authentication
- Deploying web services

**Skills:** `django-framework`, `fastapi`

---

### 03 - Data Science Agent
**Expertise:** NumPy, Pandas, Matplotlib, statistical analysis

**Use When:**
- Analyzing datasets
- Creating visualizations
- Performing statistical analysis
- Building data pipelines

**Skills:** `pandas-data-analysis`, `machine-learning`

---

### 04 - Testing & Quality Agent
**Expertise:** pytest, unittest, TDD, mocking, coverage

**Use When:**
- Writing unit/integration tests
- Setting up CI testing
- Improving code coverage
- Implementing TDD

**Skills:** `pytest-testing`, `debugging`, `security`

---

### 05 - Async & Concurrency Agent
**Expertise:** asyncio, threading, multiprocessing

**Use When:**
- Building async applications
- Optimizing I/O-bound tasks
- Parallel processing
- Real-time systems

**Skills:** `asyncio-programming`

---

### 06 - Package & Deployment Agent
**Expertise:** Poetry, Docker, PyPI, production deployment

**Use When:**
- Creating Python packages
- Publishing to PyPI
- Containerizing applications
- Production deployments

**Skills:** `poetry-packaging`

---

### 07 - Best Practices Agent
**Expertise:** PEP 8, type hints, design patterns, security

**Use When:**
- Improving code quality
- Adding type annotations
- Implementing design patterns
- Security hardening

**Skills:** `type-hints`, `security`, `python-performance`

---

### 08 - DevOps & Automation Agent
**Expertise:** CI/CD, GitHub Actions, Boto3, CLI tools

**Use When:**
- Setting up CI/CD pipelines
- AWS automation
- Building CLI tools
- Infrastructure scripting

**Skills:** `poetry-packaging`, `pytest-testing`

---

## Agent Selection Decision Tree

```
                    ┌─────────────────────┐
                    │  What are you       │
                    │  working on?        │
                    └──────────┬──────────┘
                               │
    ┌──────────┬───────────────┼───────────────┬──────────────┐
    ▼          ▼               ▼               ▼              ▼
Learning    Web App       Data Analysis    Testing      Deployment
Python?     or API?                        Code?
    │          │               │               │              │
    ▼          ▼               ▼               ▼              ▼
 Agent 01   Agent 02       Agent 03       Agent 04       Agent 06
```

## How to Get Agent Help

1. **Describe your problem** - Be specific about what you're working on
2. **Provide context** - Share your Python version, frameworks, constraints
3. **Specify your goal** - What outcome do you want to achieve?

## Example Questions

**For Agent 01 (Fundamentals):**
- "Help me understand Python decorators"
- "How do I structure a Python project?"
- "Explain list comprehensions vs generators"

**For Agent 02 (Web Development):**
- "Design a REST API for user authentication"
- "Should I use Django or FastAPI for my project?"
- "How do I handle file uploads in FastAPI?"

**For Agent 03 (Data Science):**
- "How do I handle missing data in Pandas?"
- "Create a visualization for time series data"
- "Optimize this groupby operation"

**For Agent 04 (Testing):**
- "Help me write pytest fixtures for database testing"
- "How do I mock external API calls?"
- "Set up coverage reporting in CI"

**For Agent 05 (Async):**
- "Convert this sync code to async"
- "How do I limit concurrent requests?"
- "Debug this asyncio deadlock"

**For Agent 06 (Deployment):**
- "Package my library for PyPI"
- "Create a multi-stage Dockerfile"
- "Set up Poetry for my project"

**For Agent 07 (Best Practices):**
- "Add type hints to this module"
- "Review my code for security issues"
- "Implement the repository pattern"

**For Agent 08 (DevOps):**
- "Create a GitHub Actions workflow"
- "Automate S3 uploads with Boto3"
- "Build a CLI tool with Typer"

---

## Tips for Best Results

- Be specific about Python version (3.11, 3.12, etc.)
- Share relevant code snippets
- Mention frameworks and libraries in use
- Specify constraints (performance, memory, etc.)
- Ask for trade-offs between approaches
