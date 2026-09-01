# Provider SDK - Interface

## Purpose

Defines the standard contract that all SMS providers must implement as plugins.

---

## Core Interface (Go)

```go
type Provider interface {
    Name() string

    Initialize(config ProviderConfig) error

    GetCountries() ([]Country, error)

    GetServices(country string) ([]Service, error)

    GetPrices(country, service string) ([]Price, error)

    BuyNumber(req BuyRequest) (*OrderResponse, error)

    GetSMS(orderID string) (*SMSResponse, error)

    Cancel(orderID string) error

    HealthCheck() error

    Shutdown() error
}
```

---

## Design Rules

- No provider-specific logic in core system
- All providers must be stateless or externally managed
- Must support plugin lifecycle