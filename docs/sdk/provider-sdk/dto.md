# Provider SDK - DTOs

## Country

```go
type Country struct {
    Code string
    Name string
}
```

---

## Service

```go
type Service struct {
    Code string
    Name string
}
```

---

## Price

```go
type Price struct {
    CountryCode string
    ServiceCode string
    PriceUSD    float64
    Stock       int
}
```

---

## Buy Request

```go
type BuyRequest struct {
    Country string
    Service string
    Operator string
}
```

---

## Order Response

```go
type OrderResponse struct {
    OrderID     string
    PhoneNumber string
    Status      string
}
```

---

## SMS Response

```go
type SMSResponse struct {
    OrderID string
    Code    string
    Message string
}
```