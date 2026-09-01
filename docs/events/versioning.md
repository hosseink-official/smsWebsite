# Event Versioning

## Format

All events must include version:

```json
{
  "event": "OrderCreated",
  "version": "1.0",
  "event_id": "uuid",
  "timestamp": "ISO8601",
  "payload": {}
}
```

---

## Rules

- Events are immutable
- Version changes = new event type OR backward-compatible schema update
- Consumers must ignore unknown fields