# Logging Strategy

## Format

All logs must be structured JSON.

---

## Fields

```json
{
  "timestamp": "...",
  "service": "order-service",
  "level": "info",
  "message": "order created",
  "correlation_id": "uuid"
}
```

---

## Rules

- No plain text logs
- Always include correlation_id
- No sensitive data logging