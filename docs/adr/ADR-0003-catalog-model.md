# ADR-0003: Catalog Model Design

## Status
Accepted

---

## Context

We aggregate multiple SMS providers.

Each provider has:

- different pricing
- different stock
- different service IDs

We need a unified structure.

---

## Decision

We define a **Product-Centric Catalog Model**.

A Product is the atomic unit.

---

## Product Structure

```json
{
  "product_id": "prd_xxx",
  "country": "US",
  "service": "telegram",
  "provider": "5sim",
  "provider_ref": {
    "country_id": "1",
    "service_id": "7"
  },
  "price_usd": 0.23,
  "price_local": 28500,
  "stock": 1200,
  "status": "active"
}
```

---

## Key Rules

- Catalog is READ model only
- Provider is NOT exposed to frontend
- Product is immutable snapshot per sync cycle
- Multiple providers can expose same service

---

## Consequences

### Positive
- simple frontend model
- scalable aggregation
- multi-provider comparison

### Negative
- eventual consistency
- sync complexity