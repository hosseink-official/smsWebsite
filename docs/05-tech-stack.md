# Technology Stack

This document describes the technologies used to build **smsWebsite**.

---

# Backend

| Technology | Purpose |
|------------|---------|
| Go 1.25 | Primary backend language |
| Gin | HTTP API framework |
| GORM | ORM and database access |
| PostgreSQL | Primary relational database |
| Redis | Caching and distributed locks |
| RabbitMQ | Event bus and asynchronous messaging |
| OpenAPI 3.1 | API specification |
| Swagger UI | API documentation |

---

# Frontend

| Technology | Purpose |
|------------|---------|
| React | User Interface |
| TypeScript | Type-safe frontend development |
| Vite | Build tool |
| Tailwind CSS | Styling |
| Zustand | Client state management |
| TanStack Query | Server state management |

---

# Architecture

The platform follows these architectural styles:

- Microservices Architecture
- Event-Driven Architecture
- Plugin-Based Architecture
- Hexagonal Architecture (inside each service)
- Database per Service
- API-First Design

---

# Infrastructure

| Technology | Purpose |
|------------|---------|
| Docker | Containerization |
| Docker Compose | Local development |
| Kubernetes | Production orchestration |
| Nginx | Reverse proxy |
| GitHub Actions | CI/CD |

---

# Observability

| Technology | Purpose |
|------------|---------|
| Prometheus | Metrics collection |
| Grafana | Dashboards |
| Loki | Centralized logging |
| Jaeger | Distributed tracing |
| OpenTelemetry | Telemetry instrumentation |

---

# Authentication

| Technology | Purpose |
|------------|---------|
| Auth0 | Identity Provider (Authentication) |
| Internal Auth Service | Authorization and permission management |

---

# Messaging

| Technology | Purpose |
|------------|---------|
| RabbitMQ | Domain events and asynchronous communication |

---

# Development Principles

- API-first development
- Domain-driven service boundaries
- Event-based communication
- Stateless services
- Infrastructure as Code (IaC)
- Cloud-native deployment