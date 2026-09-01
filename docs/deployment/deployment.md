# Deployment Architecture

## Runtime

- Docker containers
- Kubernetes orchestration

---

## Components

- API Gateway (Ingress)
- Microservices cluster
- Redis cluster
- PostgreSQL cluster
- RabbitMQ cluster

---

## Environments

- dev
- staging
- production

---

## CI/CD

- GitHub Actions
- Build → Test → Docker → Deploy

---

## Secrets

- Kubernetes Secrets OR Vault

---

## Scaling Strategy

- Horizontal scaling per service
- Stateless services
- Redis caching for read-heavy workloads