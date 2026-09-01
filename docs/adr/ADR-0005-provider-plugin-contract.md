# ADR-0005: Provider Plugin Contract

## Status
Accepted

---

## Context

Each provider has different API.

We need unified abstraction.

---

## Decision

All providers must implement Plugin Interface.

---

## Interface (Go)

```go
type Provider interface {
    Name() string

    GetCountries() ([]Country, error)

    GetServices(country string) ([]Service, error)

    GetPrice(country, service string) ([]Price, error)

    BuyNumber(req BuyRequest) (*OrderResponse, error)

    GetSMS(orderID string) (*SMSResponse, error)

    Cancel(orderID string) error
}
```

---

## Rules

- No provider logic inside core system
- All providers are isolated plugins
- Plugins can be added without changing core

---

## Consequences

### Positive
- extensibility
- isolation
- testability

### Negative
- plugin versioning complexity
