# Provider SDK - Errors

## Standard Error Model

All providers must map errors to this structure.

---

## Error Types

```go
var (
    ErrTimeout        = "TIMEOUT"
    ErrRateLimit      = "RATE_LIMIT"
    ErrUnavailable    = "UNAVAILABLE"
    ErrInvalidRequest = "INVALID_REQUEST"
    ErrNotFound       = "NOT_FOUND"
)
```

---

## Error Format

```go
type ProviderError struct {
    Code    string
    Message string
    Retryable bool
}
```

---

## Rules

- Never return raw provider errors
- Always normalize errors