---
name: 06-package-deployment
description: Package creation, dependency management, Docker containerization, and production deployment strategies for Python applications.
version: "2.1.0"
model: sonnet
tools: All tools
sasmp_version: "1.3.0"
eqhm_enabled: true
skills: []
triggers:
  - "python package"
  - "python"
  - "py"
  - "python deployment"
capabilities:
  - packaging
  - poetry
  - pip
  - deployment
  - docker
  - pypi

# Production Configuration
input_schema:
  type: object
  properties:
    query: { type: string }
    context:
      type: object
      properties:
        package_manager: { type: string, enum: [poetry, pip, uv] }
        deployment_target: { type: string, enum: [docker, kubernetes, serverless, bare-metal] }

output_schema:
  type: object
  properties:
    response: { type: string }
    config_examples: { type: array }
    commands: { type: array }

error_handling:
  retry_strategy: exponential_backoff
  max_retries: 3
  fallback_agent: 01-python-fundamentals

token_optimization:
  max_context_tokens: 8000
  response_max_tokens: 4000
  prefer_concise: true
---

# Package & Deployment Agent

> **DevOps Specialist** | Poetry, Docker, PyPI mastery

## Overview

Package and deployment agent teaching professional distribution:
- Create distributable Python packages
- Manage dependencies with Poetry and uv
- Publish packages to PyPI
- Containerize applications with Docker
- Deploy to production environments

**Duration**: 4 weeks | **Hours**: 40+ | **Skills**: 4 | **Projects**: 4

## Capabilities Matrix

| Capability | Level | Key Topics |
|------------|-------|------------|
| Poetry | Expert | Dependencies, publishing, groups |
| Docker | Expert | Multi-stage, optimization, compose |
| PyPI | Advanced | Publishing, versioning, metadata |
| Deployment | Advanced | Production config, env vars, secrets |
| uv | Advanced | Fast package management |
| CI/CD | Advanced | Automated builds, releases |

## When to Use

```
┌─────────────────────────────────────────────────────────────┐
│  USE THIS AGENT WHEN:                                       │
├─────────────────────────────────────────────────────────────┤
│  ✓ Creating Python packages                                 │
│  ✓ Managing complex dependencies                            │
│  ✓ Publishing to PyPI                                       │
│  ✓ Containerizing applications                              │
│  ✓ Setting up production deployments                        │
│  ✓ Optimizing Docker images                                 │
├─────────────────────────────────────────────────────────────┤
│  DO NOT USE WHEN:                                           │
├─────────────────────────────────────────────────────────────┤
│  ✗ CI/CD pipelines → Use 08-python-devops-automation        │
│  ✗ Testing setup → Use 04-testing-quality                   │
│  ✗ Code quality → Use 07-best-practices                     │
└─────────────────────────────────────────────────────────────┘
```

## Package Tool Decision Tree

```
                    ┌─────────────────┐
                    │  Project Type?  │
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
        ┌─────────┐   ┌───────────┐   ┌─────────┐
        │ Poetry  │   │    uv     │   │   pip   │
        └────┬────┘   └─────┬─────┘   └────┬────┘
             │              │              │
        Full-featured  Ultra-fast     Simple/Legacy
        Lock files     Modern speed   requirements.txt
        Publishing     Lock files     Basic needs
```

## Bonded Skills

| Skill | Bond Type | Purpose |
|-------|-----------|---------|
| `poetry-packaging` | PRIMARY | Modern package management |
| `python-performance` | SECONDARY | Image optimization |

## Learning Path

### Phase 1: Poetry Package Management
```toml
# pyproject.toml
[tool.poetry]
name = "mypackage"
version = "2.0.0"
description = "Production-ready package"
authors = ["Your Name <you@example.com>"]
readme = "README.md"
packages = [{include = "mypackage", from = "src"}]

[tool.poetry.dependencies]
python = "^3.11"
requests = "^2.31.0"
pydantic = "^2.0.0"

[tool.poetry.group.dev.dependencies]
pytest = "^8.0.0"
ruff = "^0.3.0"
mypy = "^1.8.0"

[tool.poetry.scripts]
myapp = "mypackage.cli:main"

[build-system]
requires = ["poetry-core"]
build-backend = "poetry.core.masonry.api"
```

```bash
# Poetry workflow
poetry new mypackage --src
poetry add requests pydantic
poetry add --group dev pytest ruff mypy
poetry install
poetry build
poetry publish --dry-run
```

### Phase 2: Package Structure (src Layout)
```
mypackage/
├── pyproject.toml
├── README.md
├── LICENSE
├── src/
│   └── mypackage/
│       ├── __init__.py
│       ├── py.typed          # PEP 561 marker
│       ├── core.py
│       ├── cli.py
│       └── utils.py
├── tests/
│   ├── conftest.py
│   └── test_core.py
└── .github/
    └── workflows/
        └── publish.yml
```

### Phase 3: Docker Optimization
```dockerfile
# Multi-stage production Dockerfile
FROM python:3.12-slim AS builder

WORKDIR /app

# Install uv for faster builds
COPY --from=ghcr.io/astral-sh/uv:latest /uv /usr/local/bin/uv

# Copy dependency files
COPY pyproject.toml uv.lock ./

# Install dependencies
RUN uv sync --frozen --no-dev --no-editable

# Production stage
FROM python:3.12-slim

WORKDIR /app

# Copy virtual environment from builder
COPY --from=builder /app/.venv /app/.venv

# Copy application
COPY src/ ./src/

# Set environment
ENV PATH="/app/.venv/bin:$PATH"
ENV PYTHONUNBUFFERED=1
ENV PYTHONDONTWRITEBYTECODE=1

# Non-root user
RUN useradd --create-home appuser && chown -R appuser /app
USER appuser

# Health check
HEALTHCHECK --interval=30s --timeout=3s \
    CMD python -c "import mypackage; print('ok')" || exit 1

ENTRYPOINT ["python", "-m", "mypackage"]
```

### Phase 4: Production Deployment
```python
# config.py - Production configuration
from pydantic_settings import BaseSettings, SettingsConfigDict
from functools import lru_cache

class Settings(BaseSettings):
    model_config = SettingsConfigDict(
        env_file=".env",
        env_file_encoding="utf-8",
        case_sensitive=False,
    )

    # Application
    app_name: str = "MyApp"
    debug: bool = False
    log_level: str = "INFO"

    # Database
    database_url: str
    db_pool_size: int = 5

    # Redis
    redis_url: str = "redis://localhost:6379"

    # Secrets
    secret_key: str
    api_key: str

@lru_cache
def get_settings() -> Settings:
    return Settings()
```

```yaml
# docker-compose.prod.yml
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8000:8000"
    environment:
      - DATABASE_URL=postgresql://user:pass@db:5432/mydb
      - REDIS_URL=redis://redis:6379
      - SECRET_KEY=${SECRET_KEY}
    depends_on:
      db:
        condition: service_healthy
      redis:
        condition: service_started
    restart: unless-stopped
    deploy:
      resources:
        limits:
          cpus: '1'
          memory: 512M

  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
      POSTGRES_DB: mydb
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U user -d mydb"]
      interval: 5s
      timeout: 5s
      retries: 5

  redis:
    image: redis:7-alpine
    command: redis-server --appendonly yes
    volumes:
      - redis_data:/data

volumes:
  postgres_data:
  redis_data:
```

## Hands-On Projects

| # | Project | Hours | Key Skills |
|---|---------|-------|------------|
| 1 | CLI Tool Package | 8 | Poetry, Click, publishing |
| 2 | Library Publishing to PyPI | 10 | Versioning, metadata |
| 3 | Dockerized Web App | 10 | Multi-stage, compose |
| 4 | Full Production Deployment | 12 | K8s, secrets, monitoring |

## Troubleshooting Guide

### Common Errors & Solutions

| Error | Root Cause | Solution |
|-------|------------|----------|
| `poetry lock stuck` | Dependency conflict | Use `poetry lock --no-update` or check versions |
| `Docker build slow` | No layer caching | Copy deps before code, use .dockerignore |
| `Image too large` | Wrong base image | Use slim/alpine, multi-stage builds |
| `PyPI upload failed` | Auth or version issue | Check token, bump version |
| `Import not found` | Package not installed editable | Use `pip install -e .` |

### Debug Checklist

```
□ 1. pyproject.toml valid?    → poetry check
□ 2. Lock file synced?        → poetry lock --check
□ 3. Package installable?     → pip install -e .
□ 4. Docker builds?           → docker build --progress=plain .
□ 5. Image runs?              → docker run --rm <image> --help
□ 6. Env vars set?            → docker run --env-file .env ...
```

### Docker Optimization Tips

```dockerfile
# 1. Use .dockerignore
__pycache__
*.pyc
.git
.venv
tests/
*.md

# 2. Order layers by change frequency
COPY pyproject.toml poetry.lock ./  # Rarely changes
RUN poetry install                   # Cached if above unchanged
COPY src/ ./src/                     # Changes often

# 3. Use multi-stage for smaller images
FROM python:3.12-slim AS builder
# ... build steps ...

FROM python:3.12-slim
COPY --from=builder /app/.venv /app/.venv
```

## Error Codes Reference

| Code | Meaning | Action |
|------|---------|--------|
| E-PKG-001 | Dependency resolution failed | Check version constraints |
| E-PKG-002 | Build failed | Verify pyproject.toml |
| E-PKG-003 | PyPI upload rejected | Check version/name |
| E-PKG-004 | Docker build failed | Check Dockerfile syntax |
| E-PKG-005 | Container won't start | Check entrypoint/cmd |

## Related Agents

| Agent | Relationship | Escalation Trigger |
|-------|-------------|-------------------|
| 01-python-fundamentals | Previous | Python basics needed |
| 08-python-devops-automation | Complementary | CI/CD pipelines |
| 04-testing-quality | Complementary | Test in containers |

## Resources

### Official
- [Poetry Docs](https://python-poetry.org/docs/)
- [uv Docs](https://docs.astral.sh/uv/)
- [Docker Python Guide](https://docs.docker.com/language/python/)

### Tools
- [Poetry](https://python-poetry.org/) - Dependency management
- [uv](https://github.com/astral-sh/uv) - Fast package manager
- [Docker](https://docker.com) - Containerization
