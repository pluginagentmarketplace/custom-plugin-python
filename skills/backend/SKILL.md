---
name: backend-infrastructure
description: Build scalable backend systems with Node.js, Python, databases, APIs, authentication, and cloud deployment. Use when developing server-side applications, APIs, or infrastructure systems.
---

# Backend & Infrastructure Skill

Build production-grade backend systems and APIs.

## Quick Start

Create a simple REST API with Express.js:

```javascript
import express from 'express';
import cors from 'cors';

const app = express();
app.use(cors());
app.use(express.json());

// In-memory database for demo
let users = [];

// GET all users
app.get('/api/users', (req, res) => {
  res.json(users);
});

// POST new user
app.post('/api/users', (req, res) => {
  const user = { id: Date.now(), ...req.body };
  users.push(user);
  res.status(201).json(user);
});

// GET user by ID
app.get('/api/users/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).json({ error: 'Not found' });
  res.json(user);
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

## Backend Stack Overview

### Web Frameworks
- **Express.js** (Node.js): Fast, flexible, minimal
- **FastAPI** (Python): Modern, async, auto-docs
- **Spring Boot** (Java): Enterprise-grade, feature-rich
- **Django** (Python): Full-featured with ORM

### Database Technologies
- **PostgreSQL**: Powerful relational database
- **MongoDB**: Document-based NoSQL
- **Redis**: In-memory data store for caching
- **Elasticsearch**: Search and analytics engine

### API Design
- **REST**: Industry standard API design
- **GraphQL**: Query language for APIs
- **gRPC**: High-performance RPC framework

### Authentication & Security
- **JWT**: Stateless authentication
- **OAuth 2.0**: Delegated authorization
- **bcrypt**: Password hashing
- **CORS**: Cross-origin resource sharing

### Cloud & Deployment
- **Docker**: Container technology
- **Kubernetes**: Container orchestration
- **AWS**: Cloud platform (EC2, RDS, Lambda)
- **CI/CD**: GitHub Actions, GitLab CI

## API Best Practices

### Proper HTTP Methods
```javascript
// RESTful API endpoints
GET    /api/users           // List all users
GET    /api/users/:id       // Get user by ID
POST   /api/users           // Create user
PUT    /api/users/:id       // Update user
DELETE /api/users/:id       // Delete user
PATCH  /api/users/:id       // Partial update
```

### Error Handling
```javascript
// Structured error responses
{
  "error": "Bad Request",
  "code": 400,
  "message": "Email is required",
  "timestamp": "2025-11-18T22:30:00Z"
}
```

### Database Connection
```python
# Using SQLAlchemy with FastAPI
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker

DATABASE_URL = "postgresql://user:password@localhost/dbname"
engine = create_engine(DATABASE_URL)
SessionLocal = sessionmaker(bind=engine)

def get_db():
    db = SessionLocal()
    try:
        yield db
    finally:
        db.close()
```

## Scaling Strategies

1. **Horizontal Scaling**: Add more server instances
2. **Caching Layer**: Redis for frequent queries
3. **Database Optimization**: Indexing, query optimization
4. **Load Balancing**: Distribute traffic across servers
5. **Asynchronous Processing**: Background jobs, message queues

## Security Essentials

✅ Use HTTPS for all communications
✅ Validate all user inputs
✅ Use parameterized queries to prevent SQL injection
✅ Implement rate limiting
✅ Hash passwords with bcrypt
✅ Use environment variables for secrets
✅ Implement proper logging and monitoring

## Learning Resources

- [Express.js Documentation](https://expressjs.com)
- [FastAPI Documentation](https://fastapi.tiangolo.com)
- [PostgreSQL Documentation](https://www.postgresql.org/docs)
- [RESTful API Design Best Practices](https://restfulapi.net)
- [Backend Masters Course](https://www.udemy.com/course/nodejs-complete-guide)

## Practice Projects

1. **Beginner**: Blog API with CRUD operations
2. **Intermediate**: Social media backend with authentication
3. **Advanced**: E-commerce platform with payment integration

## Monitoring & Observability

- **Logging**: Winston, Morgan, Pino
- **Monitoring**: Prometheus, Grafana
- **Tracing**: Jaeger, Zipkin
- **APM**: DataDog, New Relic
