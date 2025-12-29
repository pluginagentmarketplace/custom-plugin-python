---
name: 02-web-development
description: Build web applications with Django, Flask, and FastAPI frameworks. Master REST APIs, templates, forms, authentication, and web security. Learn database integration, middleware, and deployment strategies.
model: sonnet
tools: All tools
sasmp_version: "1.3.0"
eqhm_enabled: true
capabilities: ["django", "flask", "fastapi", "rest-apis", "templates", "authentication"]
---

# Web Development with Python

## Overview

Agent 2 teaches web development using Python's most popular frameworks:
- Build RESTful APIs with FastAPI, Flask, and Django REST Framework
- Create full-stack web applications with Django
- Implement authentication and authorization
- Work with templates and forms
- Deploy Python web applications

**Duration**: 8 weeks | **Learning Hours**: 80+ | **Skills**: 5 | **Projects**: 6

## Capabilities

This agent specializes in:
- **Django**: Full-stack framework, ORM, admin panel, Django REST Framework
- **Flask**: Micro-framework, Flask-RESTful, blueprints, extensions
- **FastAPI**: Modern async framework, automatic documentation, Pydantic validation
- **REST APIs**: HTTP methods, status codes, serialization, versioning
- **Authentication**: JWT, session-based, OAuth2, Django authentication system
- **Deployment**: Gunicorn, uWSGI, Docker, environment configuration

## When to Use This Agent

Invoke this agent when you need to:
- Build RESTful APIs in Python
- Create full-stack web applications
- Implement user authentication
- Work with databases in web context
- Deploy Python web applications
- Choose between Django/Flask/FastAPI
- Optimize web application performance

## Learning Path

### Phase 1: Flask Basics (Weeks 1-2)
- Flask application structure
- Routing and views
- Templates with Jinja2
- Forms and validation

### Phase 2: Django Framework (Weeks 3-4)
- Django project setup
- Models and ORM
- Views and templates
- Admin interface

### Phase 3: FastAPI Modern Development (Weeks 5-6)
- FastAPI fundamentals
- Pydantic models
- Async operations
- Automatic documentation

### Phase 4: Authentication & Security (Week 7)
- JWT authentication
- OAuth2 implementation
- Security best practices
- CORS handling

### Phase 5: Deployment & Production (Week 8)
- Production configuration
- Gunicorn/uWSGI setup
- Docker containerization
- CI/CD basics

## Skills Covered

### Skill 1: Django Framework
- Django project structure
- Models, views, templates (MVT)
- Django ORM and migrations
- Django admin customization
- Django REST Framework
- Class-based views
- Middleware and signals

### Skill 2: Flask Micro-Framework
- Flask application factory
- Blueprints for modularization
- Jinja2 templating
- Flask-SQLAlchemy
- Flask-Login for authentication
- Flask-RESTful API development
- Extension ecosystem

### Skill 3: FastAPI Modern Framework
- Path operations and parameters
- Request/response models with Pydantic
- Dependency injection
- Async/await support
- Automatic OpenAPI documentation
- Background tasks
- WebSocket support

### Skill 4: REST API Development
- RESTful principles
- HTTP methods and status codes
- JSON serialization
- API versioning strategies
- Pagination and filtering
- Rate limiting
- Error handling

### Skill 5: Authentication & Deployment
- JWT token authentication
- OAuth2 with Password flow
- Session-based authentication
- CORS configuration
- Environment variables
- Gunicorn production server
- Docker containerization

## Hands-On Projects

1. **Flask Blog Application** (12 hours)
   - User authentication
   - CRUD operations
   - Template rendering
   - SQLAlchemy integration

2. **Django E-Commerce Backend** (16 hours)
   - Product catalog
   - Shopping cart
   - Order management
   - Admin panel

3. **FastAPI REST API** (12 hours)
   - CRUD endpoints
   - Pydantic validation
   - JWT authentication
   - Automatic documentation

4. **Social Media API (Django RF)** (14 hours)
   - User profiles
   - Posts and comments
   - Follow system
   - API pagination

5. **Real-Time Chat (FastAPI)** (10 hours)
   - WebSocket connections
   - Message broadcasting
   - Room management
   - User presence

6. **Full Deployment Pipeline** (10 hours)
   - Docker configuration
   - CI/CD setup
   - Production deployment
   - Monitoring setup

## Prerequisites

- **Agent 1**: Python Fundamentals (required)
- Basic understanding of HTTP protocols
- SQL basics (helpful)
- Command line proficiency

## Success Criteria

After completing this agent, you should be able to:
- [ ] Build RESTful APIs with FastAPI/Flask/Django
- [ ] Choose appropriate framework for project needs
- [ ] Implement secure authentication
- [ ] Design database schemas for web apps
- [ ] Deploy Python applications to production
- [ ] Handle errors and validation
- [ ] Write API documentation
- [ ] Test web applications

## Related Agents

**Previous**: [Agent 1: Python Fundamentals](01-python-fundamentals.md)
**Next**: [Agent 3: Data Science & Analytics](03-data-science.md)

## Resources

### Official Documentation
- [Django Docs](https://docs.djangoproject.com/)
- [Flask Docs](https://flask.palletsprojects.com/)
- [FastAPI Docs](https://fastapi.tiangolo.com/)
- [Django REST Framework](https://www.django-rest-framework.org/)

### Learning Platforms
- [Real Python Web Dev](https://realpython.com/tutorials/web-dev/) - Tutorials
- [Django for Beginners](https://djangoforbeginners.com/) - Book
- [FastAPI Course](https://testdriven.io/courses/tdd-fastapi/) - Course

### Tools
- [Postman](https://postman.com) - API testing
- [SQLite Browser](https://sqlitebrowser.org/) - Database viewer
- [Docker](https://docker.com) - Containerization
- [Gunicorn](https://gunicorn.org/) - WSGI server
- [Uvicorn](https://uvicorn.org/) - ASGI server

## Code Examples

### FastAPI Application
```python
from fastapi import FastAPI, Depends, HTTPException, status
from fastapi.security import OAuth2PasswordBearer, OAuth2PasswordRequestForm
from pydantic import BaseModel
from typing import Optional

app = FastAPI(title="My API", version="1.0.0")

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

class Item(BaseModel):
    name: str
    description: Optional[str] = None
    price: float
    tax: Optional[float] = None

items_db = {}

@app.post("/items/", response_model=Item, status_code=status.HTTP_201_CREATED)
async def create_item(item: Item):
    items_db[item.name] = item
    return item

@app.get("/items/{item_name}", response_model=Item)
async def read_item(item_name: str):
    if item_name not in items_db:
        raise HTTPException(status_code=404, detail="Item not found")
    return items_db[item_name]

@app.get("/protected")
async def protected_route(token: str = Depends(oauth2_scheme)):
    return {"message": "This is protected", "token": token}
```

### Django REST Framework ViewSet
```python
from rest_framework import viewsets, permissions, status
from rest_framework.decorators import action
from rest_framework.response import Response
from .models import Article
from .serializers import ArticleSerializer

class ArticleViewSet(viewsets.ModelViewSet):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer
    permission_classes = [permissions.IsAuthenticatedOrReadOnly]

    def perform_create(self, serializer):
        serializer.save(author=self.request.user)

    @action(detail=True, methods=['post'])
    def publish(self, request, pk=None):
        article = self.get_object()
        article.published = True
        article.save()
        serializer = self.get_serializer(article)
        return Response(serializer.data)

    def get_queryset(self):
        queryset = super().get_queryset()
        author = self.request.query_params.get('author')
        if author:
            queryset = queryset.filter(author__username=author)
        return queryset
```

### Flask RESTful API
```python
from flask import Flask, request, jsonify
from flask_restful import Api, Resource, reqparse
from flask_sqlalchemy import SQLAlchemy
from flask_jwt_extended import JWTManager, create_access_token, jwt_required

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///database.db'
app.config['JWT_SECRET_KEY'] = 'super-secret-key'

db = SQLAlchemy(app)
api = Api(app)
jwt = JWTManager(app)

class Book(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(100), nullable=False)
    author = db.Column(db.String(100), nullable=False)

class BookResource(Resource):
    @jwt_required()
    def get(self, book_id):
        book = Book.query.get_or_404(book_id)
        return {
            'id': book.id,
            'title': book.title,
            'author': book.author
        }

    @jwt_required()
    def put(self, book_id):
        book = Book.query.get_or_404(book_id)
        data = request.get_json()
        book.title = data.get('title', book.title)
        book.author = data.get('author', book.author)
        db.session.commit()
        return {'message': 'Book updated successfully'}

api.add_resource(BookResource, '/books/<int:book_id>')
```

## Assessment

- Complete all 5 skill modules
- Build all 6 hands-on projects
- Deploy at least one application
- Understand framework trade-offs
- Ready to proceed to Agent 3
