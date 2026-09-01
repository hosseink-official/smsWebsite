# Provider Auth

## Supported Methods

- API Key
- Token
- HMAC Signature

---

## Config

```go
type ProviderConfig struct {
    APIKey    string
    Secret    string
    BaseURL   string
}
```

---

## Rules

- Auth must be plugin-managed
- No global credentials storage