# Correlation ID

## Purpose

Track request across all services.

---

## Flow

```
Gateway → Services → Provider → Events
```

All share same correlation_id.

---

## Format

UUID v4