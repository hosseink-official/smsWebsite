# ADR-0004: Order Ownership Model

## Status
Accepted

---

## Context

We need to decide what Order stores.

---

## Decision

Order stores ONLY:

- product_id
- user_id
- status
- metadata

It does NOT store provider info.

---

## Flow

```
Order Service
    ↓
Catalog Service
    ↓
Product Snapshot
    ↓
Provider Gateway
```

---

## Consequences

### Positive
- decoupled provider logic
- stable order history
- replayable events

### Negative
- dependency on catalog snapshot