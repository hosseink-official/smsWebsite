# ADR-0002: Provider Plugin System

## Status
Accepted

---

## Context

Providers have different APIs:

- different request formats
- different response formats
- different authentication methods

---

## Decision

All providers will be implemented as **Plugins**.

Each plugin must implement a standard interface:

```go
type Provider interface {
    GetCountries()
    GetServices()
    GetPrices()
    BuyNumber()
    GetSMS()
    Cancel()
}
```

---

## Consequences

### Positive

- easy to add new providers
- isolated provider logic
- no core system changes needed

### Negative

- plugin version management required
- abstraction overhead