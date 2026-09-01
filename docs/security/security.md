# Security Model

## Authentication

- Auth0 used as Identity Provider
- Internal JWT issued per session

---

## Authorization

- Role Based Access Control (RBAC)

Roles:
- user
- admin
- system
- provider-plugin

---

## Service-to-Service Security

- JWT between services
- Optional mTLS in Kubernetes

---

## Rate Limiting

- API Gateway level
- Per user limits
- Per IP limits

---

## Abuse Prevention

- Fraud detection rules
- Provider spam protection
- Wallet anomaly detection