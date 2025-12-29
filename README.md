<div align="center">

# Python Developer Plugin

### Complete Python Development Mastery for Claude Code

**Master Python from fundamentals to advanced topics: Django, FastAPI, Pandas, pytest, async programming, and performance optimization with 7 specialized agents and 7 production-ready skills**

[![Verified](https://img.shields.io/badge/Verified-Working-success?style=flat-square&logo=checkmarx)](https://github.com/pluginagentmarketplace/custom-plugin-python)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)
[![Version](https://img.shields.io/badge/Version-2.0.0-blue?style=flat-square)](https://github.com/pluginagentmarketplace/custom-plugin-python)
[![Status](https://img.shields.io/badge/Status-Production_Ready-brightgreen?style=flat-square)](https://github.com/pluginagentmarketplace/custom-plugin-python)
[![Agents](https://img.shields.io/badge/Agents-7-orange?style=flat-square)](#agents-overview)
[![Skills](https://img.shields.io/badge/Skills-7-purple?style=flat-square)](#skills-reference)
[![SASMP](https://img.shields.io/badge/SASMP-v1.3.0-blueviolet?style=flat-square)](#)

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](skills/python-fundamentals/)
[![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)](skills/django-framework/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](skills/pandas-data-analysis/)
[![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=for-the-badge&logo=pytest&logoColor=white)](skills/pytest-testing/)

[Quick Start](#quick-start) | [Agents](#agents-overview) | [Skills](#skills-reference) | [Commands](#commands)

</div>

---

## Verified Installation

> **This plugin has been tested and verified working on Claude Code.**
> Last verified: December 2025

---

## Quick Start

### Option 1: Install from GitHub (Recommended)

```bash
# Step 1: Add the marketplace from GitHub
/plugin add marketplace pluginagentmarketplace/custom-plugin-python

# Step 2: Install the plugin
/plugin install python-developer-plugin@pluginagentmarketplace-python

# Step 3: Restart Claude Code to load new plugins
```

### Option 2: Clone and Load Locally

```bash
# Clone the repository
git clone https://github.com/pluginagentmarketplace/custom-plugin-python.git

# Navigate to the directory in Claude Code
cd custom-plugin-python

# Load the plugin
/plugin load .
```

After loading, restart Claude Code.

### Verify Installation

After restarting Claude Code, verify the plugin is loaded. You should see these agents available:

```
custom-plugin-python:01-python-fundamentals
custom-plugin-python:02-web-development
custom-plugin-python:03-data-science
custom-plugin-python:04-testing-quality
custom-plugin-python:05-async-concurrency
custom-plugin-python:06-package-deployment
custom-plugin-python:07-best-practices
```

---

## Available Skills

Once installed, these 7 skills become available:

| Skill | Invoke Command | Description |
|-------|----------------|-------------|
| Asyncio Programming | `Skill("python-developer-plugin:asyncio-programming")` | async/await, coroutines |
| Django Framework | `Skill("python-developer-plugin:django-framework")` | ORM, REST, authentication |
| Pandas Data Analysis | `Skill("python-developer-plugin:pandas-data-analysis")` | DataFrames, cleaning, viz |
| Poetry Packaging | `Skill("python-developer-plugin:poetry-packaging")` | Dependencies, PyPI publish |
| Pytest Testing | `Skill("python-developer-plugin:pytest-testing")` | Fixtures, mocking, TDD |
| Python Fundamentals | `Skill("python-developer-plugin:python-fundamentals")` | Syntax, OOP, stdlib |
| Python Performance | `Skill("python-developer-plugin:python-performance")` | Profiling, optimization |

---

## What This Plugin Does

This plugin provides **7 specialized agents** and **7 production-ready skills** covering 460+ hours of Python development content:

| Agent | Hours | Purpose |
|-------|-------|---------|
| **Python Fundamentals** | 60h | Syntax, OOP, standard library |
| **Web Development** | 80h | Django, Flask, FastAPI |
| **Data Science** | 100h | Pandas, NumPy, Scikit-learn |
| **Testing Quality** | 50h | pytest, TDD, coverage |
| **Async Concurrency** | 60h | asyncio, aiohttp |
| **Package Deployment** | 40h | Poetry, Docker, CI/CD |
| **Best Practices** | 70h | PEP 8, design patterns |

---

## Agents Overview

### 7 Implementation Agents

Each agent is designed to **do the work**, not just explain:

| Agent | Capabilities | Example Prompts |
|-------|--------------|-----------------|
| **Fundamentals** | Syntax, OOP, stdlib | `"Python classes"`, `"Type hints"` |
| **Web** | Django, Flask, FastAPI | `"Django API"`, `"FastAPI setup"` |
| **Data Science** | Pandas, NumPy, viz | `"Pandas analysis"`, `"DataFrame"` |
| **Testing** | pytest, TDD, coverage | `"Write tests"`, `"Fixtures"` |
| **Async** | asyncio, concurrency | `"Async function"`, `"Event loop"` |
| **Packaging** | Poetry, Docker, PyPI | `"Poetry project"`, `"Publish"` |
| **Best Practices** | PEP 8, patterns | `"Code review"`, `"Optimization"` |

---

## Commands

4 interactive commands for Python development workflows:

| Command | Usage | Description |
|---------|-------|-------------|
| `/roadmap` | `/roadmap` | Choose Python learning path |
| `/agent-guide` | `/agent-guide` | Connect with Python experts |
| `/skill-assessment` | `/skill-assessment` | Evaluate Python proficiency |
| `/project-builder` | `/project-builder` | Build practical projects |

---

## Skills Reference

Each skill includes **Golden Format** content:
- `assets/` - Configuration templates and setup files
- `scripts/` - Automation and validation scripts
- `references/` - Methodology guides and best practices

### All 7 Skills by Category

| Category | Skills |
|----------|--------|
| **Core** | python-fundamentals |
| **Web** | django-framework |
| **Data** | pandas-data-analysis |
| **Testing** | pytest-testing |
| **Async** | asyncio-programming |
| **Packaging** | poetry-packaging |
| **Performance** | python-performance |

---

## Usage Examples

### Example 1: Create Django REST API

```python
# Before: Manual API creation

# After (with Web Development agent):
Skill("python-developer-plugin:django-framework")

# Generates:
# - Django project structure
# - DRF viewsets and serializers
# - Authentication setup
# - Database models
```

### Example 2: Data Analysis with Pandas

```python
# Before: Manual data processing

# After (with Data Science agent):
Skill("python-developer-plugin:pandas-data-analysis")

# Provides:
# - DataFrame operations
# - Data cleaning patterns
# - Visualization code
# - Aggregation examples
```

### Example 3: pytest Test Suite

```python
# Before: No tests

# After (with Testing agent):
Skill("python-developer-plugin:pytest-testing")

# Creates:
# - Fixture patterns
# - Mocking examples
# - Parametrized tests
# - Coverage configuration
```

---

## Plugin Structure

```
custom-plugin-python/
├── .claude-plugin/
│   ├── plugin.json           # Plugin manifest
│   └── marketplace.json      # Marketplace config
├── agents/                   # 7 specialized agents
│   ├── 01-python-fundamentals.md
│   ├── 02-web-development.md
│   ├── 03-data-science.md
│   ├── 04-testing-quality.md
│   ├── 05-async-concurrency.md
│   ├── 06-package-deployment.md
│   └── 07-best-practices.md
├── skills/                   # 7 skills (Golden Format)
│   ├── asyncio-programming/SKILL.md
│   ├── django-framework/SKILL.md
│   ├── pandas-data-analysis/SKILL.md
│   ├── poetry-packaging/SKILL.md
│   ├── pytest-testing/SKILL.md
│   ├── python-fundamentals/SKILL.md
│   └── python-performance/SKILL.md
├── commands/                 # 4 slash commands
│   ├── agent-guide.md
│   ├── project-builder.md
│   ├── roadmap.md
│   └── skill-assessment.md
├── hooks/hooks.json
├── README.md
├── CHANGELOG.md
└── LICENSE
```

---

## Technology Coverage

| Category | Technologies |
|----------|--------------|
| **Core** | Python 3.9-3.12, Type Hints |
| **Web** | Django 4.x, Flask 3.x, FastAPI |
| **Data** | Pandas 2.x, NumPy, Matplotlib, Scikit-learn |
| **Testing** | pytest 7.x, unittest, coverage |
| **Async** | asyncio, aiohttp, uvloop |
| **Packaging** | Poetry, pip, setuptools, twine |
| **Performance** | cProfile, memory_profiler, Numba |

---

## Learning Paths

| Path | Duration | Focus |
|------|----------|-------|
| Fundamentals | 6 weeks | Python syntax, OOP, stdlib |
| Web Developer | 8 weeks | Django, Flask, FastAPI |
| Data Scientist | 10 weeks | Pandas, NumPy, ML |
| Quality Engineer | 5 weeks | pytest, TDD, coverage |

### Recommended Sequence
1. Python Fundamentals (6 weeks)
2. Choose specialization (8-10 weeks)
3. Advanced topics (6-7 weeks)
4. Mastery and open source

---

## Requirements

| Requirement | Version |
|-------------|---------|
| Python | 3.9+ (3.11+ recommended) |
| pip/Poetry | Latest |
| Claude Code | Latest |

---

## Metadata

| Field | Value |
|-------|-------|
| **Last Updated** | 2025-12-28 |
| **Maintenance Status** | Active |
| **SASMP Version** | 1.3.0 |
| **Support** | [Issues](../../issues) |

---

## License

MIT License - See [LICENSE](LICENSE) for details.

---

## Contributing

Contributions are welcome:

1. Fork the repository
2. Create a feature branch
3. Follow the Golden Format for new skills
4. Submit a pull request

---

## Contributors

**Authors:**
- **Dr. Umit Kacar** - Senior AI Researcher & Engineer
- **Muhsin Elcicek** - Senior Software Architect

---

<div align="center">

**Master Python development with AI assistance!**

[![Made for Python](https://img.shields.io/badge/Made%20for-Python%20Developers-3776AB?style=for-the-badge&logo=python)](https://github.com/pluginagentmarketplace/custom-plugin-python)

**Built by Dr. Umit Kacar & Muhsin Elcicek**

*Based on [roadmap.sh/python](https://roadmap.sh/python)*

</div>
