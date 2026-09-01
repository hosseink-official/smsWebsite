# API Overview

## Style

- REST API
- JSON only
- Versioned: /api/v1/

---

## Gateway Routes

```
/api/v1/auth/*
/api/v1/catalog/*
/api/v1/orders/*
/api/v1/wallet/*
/api/v1/sms/*
```

---

## Example Response

```json
{
  "success": true,
  "data": {},
  "error": null
}
```

---

## Error Format

```json
{
  "success": false,
  "error": {
    "code": "ORDER_FAILED",
    "message": "Provider unavailable"
  }
}
```