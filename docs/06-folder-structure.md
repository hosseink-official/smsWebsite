# Folder Structure

smsWebsite is organized as a Go monorepo.

The repository separates deployable applications, shared libraries, provider plugins, infrastructure and documentation.

---

# Repository Structure

```text
smsWebsite/

├── apps/
│   ├── api-gateway/
│   ├── auth-service/
│   ├── catalog-service/
│   ├── offer-engine-service/
│   ├── order-service/
│   ├── wallet-service/
│   ├── sms-service/
│   ├── scheduler-service/

├── packages/
│   ├── shared/
│   ├── logger/
│   ├── config/
│   ├── postgres/
│   ├── redis/
│   ├── rabbitmq/
│   ├── auth-common/
│   ├── events/
│   └── provider-sdk/

├── plugins/
│   └── providers/
│       ├── fivesim/
│       ├── smsman/
│       ├── onlinesim/
│       └── herosms/

├── docs/

├── deployments/
│   ├── docker/
│   └── kubernetes/

├── scripts/

├── .github/

├── Makefile

├── Taskfile.yml

└── README.md
```

---

# Service Layout (Go)

Each service follows the same internal structure.

```text
service/

├── cmd/

├── internal/
│   ├── domain/
│   ├── application/
│   ├── infrastructure/
│   └── interfaces/

├── configs/

├── migrations/

├── tests/

├── go.mod

└── Dockerfile
```

---

# Directory Responsibilities

## apps/

Contains all deployable microservices.

Each service owns:

- its business logic
- its database
- its API
- its events

---

## packages/

Reusable libraries shared between services.

Packages must remain framework-independent whenever possible.

---

## plugins/

Contains Provider SDK implementations.

Each provider is isolated in its own module.

---

## docs/

Contains all architecture, ADRs, API specifications, diagrams and operational documentation.

---

## deployments/

Infrastructure deployment files.

Includes:

- Docker Compose
- Kubernetes manifests

---

## scripts/

Development and automation scripts.

Examples:

- database migrations
- code generation
- release scripts

---

# Design Principles

- Monorepo
- Microservices
- Database per Service
- Plugin-Based Providers
- Event-Driven Communication
- Shared Libraries
- Independent Deployments