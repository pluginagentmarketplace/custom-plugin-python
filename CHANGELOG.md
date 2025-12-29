# Changelog

All notable changes to the Python Developer Plugin will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [2.0.0] - 2025-12-28

### Added
- marketplace.json for plugin marketplace compatibility
- SASMP v1.3.0 compliance for all agents
- Template v2.1.0 README format (18 required sections)
- Verified Installation notice
- Available Skills table with `Skill("...")` invoke syntax
- Usage Examples section
- Plugin Structure directory tree
- Technology Coverage table

### Changed
- plugin.json restructured to new format (paths, author object, repository string)
- README completely rewritten to template v2.1.0
- Quick Start commands fixed (`/plugin add marketplace` format)
- Version bump from 1.0.0 to 2.0.0
- hooks.json standardized to `{"hooks": {}}`

### Fixed
- E307: plugin.json repository format (object to string)
- E303: marketplace.name differs from plugin.name

---

## [1.0.0] - 2024-11-20

### Initial Release

**7 Python Specialist Agents**
- Python Fundamentals (syntax, OOP, stdlib)
- Web Development (Django, Flask, FastAPI)
- Data Science (Pandas, NumPy, Scikit-learn)
- Testing Quality (pytest, TDD, coverage)
- Async Concurrency (asyncio, aiohttp)
- Package Deployment (Poetry, Docker, CI/CD)
- Best Practices (PEP 8, design patterns)

**7 Core Skills**
- asyncio-programming
- django-framework
- pandas-data-analysis
- poetry-packaging
- pytest-testing
- python-fundamentals
- python-performance

**4 Interactive Commands**
- /roadmap, /agent-guide, /skill-assessment, /project-builder

**Content**: 460+ hours, 30+ projects

**Status**: Production Ready

---

## Contributors

- **Dr. Umit Kacar** - Senior AI Researcher & Engineer
- **Muhsin Elcicek** - Senior Software Architect

---

*Last Updated: 2025-12-28*
