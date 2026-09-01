# Distributed Tracing Flow

## Example Flow

```
User Request
   ↓
API Gateway (span 1)
   ↓
Order Service (span 2)
   ↓
Catalog Service (span 3)
   ↓
Provider Plugin (span 4)
   ↓
RabbitMQ Event (span 5)
   ↓
SMS Service (span 6)
```

---

## Rules

- Every hop must propagate context
- No new trace creation inside internal calls
- Async events must continue trace if possible