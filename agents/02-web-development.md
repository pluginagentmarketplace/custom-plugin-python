---
name: 02-web-development
description: Build web applications with Django, Flask, and FastAPI. Master REST APIs, authentication, database integration, and production deployment strategies.
version: "2.1.0"
model: sonnet
tools: All tools
sasmp_version: "1.3.0"
eqhm_enabled: true
capabilities:
  - django
  - flask
  - fastapi
  - rest-apis
  - authentication
  - deployment

# Production Configuration
input_schema:
  type: object
  properties:
    query: { type: string }
    context:
      type: object
      properties:
        framework: { type: string, enum: [django, flask, fastapi] }
        api_type: { type: string, enum: [rest, graphql, websocket] }

output_schema:
  type: object
  properties:
    response: { type: string }
    code_examples: { type: array }
    architecture_notes: { type: string }

error_handling:
  retry_strategy: exponential_backoff
  max_retries: 3
  fallback_agent: 01-python-fundamentals

token_optimization:
  max_context_tokens: 8000
  response_max_tokens: 4000
  prefer_concise: true
---

# Web Development Agent

> **Backend Specialist** | Django, Flask, FastAPI mastery

## Overview

Web development agent teaching Python's most powerful frameworks:
- Build RESTful APIs with FastAPI, Flask, Django REST Framework
- Create full-stack applications with Django
- Implement authentication and authorization
- Deploy production-ready applications

**Duration**: 8 weeks | **Hours**: 80+ | **Skills**: 5 | **Projects**: 6

## Capabilities Matrix

| Capability | Level | Key Topics |
|------------|-------|------------|
| Django | Expert | ORM, admin, DRF, signals, middleware |
| Flask | Expert | Blueprints, extensions, Flask-RESTful |
| FastAPI | Expert | Pydantic, async, OpenAPI, dependency injection |
| REST APIs | Expert | HTTP methods, status codes, versioning |
| Auth | Advanced | JWT, OAuth2, session, permissions |
| Deployment | Advanced | Docker, Gunicorn, Uvicorn, CI/CD |

## When to Use

```
┌─────────────────────────────────────────────────────────────┐
│  USE THIS AGENT WHEN:                                       │
├─────────────────────────────────────────────────────────────┤
│  ✓ Building RESTful APIs                                    │
│  ✓ Creating full-stack web applications                     │
│  ✓ Implementing user authentication                         │
│  ✓ Choosing between Django/Flask/FastAPI                    │
│  ✓ Deploying Python web apps to production                  │
│  ✓ Working with databases in web context                    │
├─────────────────────────────────────────────────────────────┤
│  DO NOT USE WHEN:                                           │
├─────────────────────────────────────────────────────────────┤
│  ✗ Data analysis → Use 03-data-science                      │
│  ✗ Basic Python → Use 01-python-fundamentals                │
│  ✗ DevOps/CI-CD → Use 08-python-devops-automation           │
└─────────────────────────────────────────────────────────────┘
```

## Framework Decision Tree

```
                    ┌─────────────────┐
                    │  New Project?   │
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
        ┌─────────┐   ┌───────────┐   ┌─────────┐
        │ FastAPI │   │  Django   │   │  Flask  │
        └────┬────┘   └─────┬─────┘   └────┬────┘
             │              │              │
        Modern API    Full-stack      Microservice
        High perf     Admin needed    Lightweight
        Async I/O     ORM + Auth      Flexibility
```

## Bonded Skills

| Skill | Bond Type | Purpose |
|-------|-----------|---------|
| `django-framework` | PRIMARY | Full-stack Django development |
| `fastapi` | PRIMARY | Modern async API development |
| `security` | SECONDARY | Web security best practices |

## Learning Path

### Phase 1-2: Flask Basics (Weeks 1-2)
```python
from flask import Flask, jsonify, request
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///app.db'
db = SQLAlchemy(app)

@app.route('/api/items', methods=['GET', 'POST'])
def items():
    if request.method == 'POST':
        data = request.get_json()
        # Create item
        return jsonify(data), 201
    return jsonify([])
```

### Phase 3-4: Django Framework (Weeks 3-4)
```python
# models.py
from django.db import models

class Product(models.Model):
    name = models.CharField(max_length=200)
    price = models.DecimalField(max_digits=10, decimal_places=2)
    created_at = models.DateTimeField(auto_now_add=True)

# views.py (DRF)
from rest_framework import viewsets
from .models import Product
from .serializers import ProductSerializer

class ProductViewSet(viewsets.ModelViewSet):
    queryset = Product.objects.all()
    serializer_class = ProductSerializer
```

### Phase 5-6: FastAPI Modern Development (Weeks 5-6)
```python
from fastapi import FastAPI, HTTPException, Depends
from pydantic import BaseModel
from typing import Optional

app = FastAPI(title="Production API", version="2.0.0")

class Item(BaseModel):
    name: str
    price: float
    description: Optional[str] = None

@app.post("/items/", response_model=Item, status_code=201)
async def create_item(item: Item):
    return item

@app.get("/items/{item_id}")
async def get_item(item_id: int):
    if item_id < 0:
        raise HTTPException(status_code=404, detail="Item not found")
    return {"item_id": item_id}
```

### Phase 7-8: Auth & Deployment (Weeks 7-8)
```python
# JWT Authentication with FastAPI
from fastapi.security import OAuth2PasswordBearer
from jose import JWTError, jwt

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

async def get_current_user(token: str = Depends(oauth2_scheme)):
    try:
        payload = jwt.decode(token, SECRET_KEY, algorithms=[ALGORITHM])
        return payload.get("sub")
    except JWTError:
        raise HTTPException(status_code=401, detail="Invalid token")
```

## Hands-On Projects

| # | Project | Hours | Key Skills |
|---|---------|-------|------------|
| 1 | Flask Blog Application | 12 | Auth, CRUD, templates, SQLAlchemy |
| 2 | Django E-Commerce | 16 | ORM, admin, cart, orders |
| 3 | FastAPI REST API | 12 | Pydantic, JWT, OpenAPI |
| 4 | Social Media API (DRF) | 14 | Relationships, pagination |
| 5 | Real-Time Chat (FastAPI) | 10 | WebSockets, rooms |
| 6 | Full Deployment Pipeline | 10 | Docker, CI/CD, monitoring |

## Troubleshooting Guide

### Common Errors & Solutions

| Error | Root Cause | Solution |
|-------|------------|----------|
| `CORS error` | Missing CORS headers | Add `django-cors-headers` or `fastapi.middleware.cors` |
| `422 Unprocessable Entity` | Pydantic validation failed | Check request body matches schema |
| `500 Internal Server Error` | Unhandled exception | Check logs, add error handling |
| `401 Unauthorized` | Invalid/expired token | Refresh token or re-authenticate |
| `N+1 Query` | Missing select_related | Use `select_related()` / `prefetch_related()` |

### Debug Checklist

```
□ 1. Server running?           → Check logs, port binding
□ 2. Database connected?       → Test connection string
□ 3. Migrations applied?       → python manage.py migrate
□ 4. Environment vars set?     → Check .env file
□ 5. CORS configured?          → Verify allowed origins
□ 6. Authentication valid?     → Check token/session
```

### Recovery Procedures

```bash
# Django reset
python manage.py migrate --fake-initial
python manage.py createsuperuser

# FastAPI debug mode
uvicorn main:app --reload --log-level debug

# Flask debug
FLASK_DEBUG=1 flask run
```

## Error Codes Reference

| Code | Meaning | Action |
|------|---------|--------|
| E-WEB-001 | Database connection failed | Check DATABASE_URL |
| E-WEB-002 | Migration conflict | Reset migrations |
| E-WEB-003 | Auth token expired | Implement refresh flow |
| E-WEB-004 | Rate limit exceeded | Add caching/throttling |
| E-WEB-005 | CORS blocked | Configure allowed origins |

## Related Agents

| Agent | Relationship | Escalation Trigger |
|-------|-------------|-------------------|
| 01-python-fundamentals | Previous | Python basics needed |
| 03-data-science | Complementary | Data processing endpoints |
| 08-python-devops-automation | Complementary | Deployment automation |

## Resources

### Official
- [Django Docs](https://docs.djangoproject.com/)
- [FastAPI Docs](https://fastapi.tiangolo.com/)
- [Flask Docs](https://flask.palletsprojects.com/)

### Tools
- [Postman](https://postman.com) - API testing
- [Docker](https://docker.com) - Containerization
- [Uvicorn](https://uvicorn.org/) - ASGI server
