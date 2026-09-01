# ADR-0001: Marketplace vs Provider Model

## Status
Accepted

---

## Context

SMS systems are usually built as direct provider integrations.

This leads to:

- tight coupling
- duplication of logic
- hard scaling
- inconsistent data

---

## Decision

smsWebsite will be built as a:

> Marketplace Aggregator, NOT a Provider system

---

## Consequences

### Positive

- scalable provider integration
- unified catalog
- easier expansion
- better user experience

---

### Negative

- more complex architecture
- requires sync layer
- eventual consistency instead of real-time truth