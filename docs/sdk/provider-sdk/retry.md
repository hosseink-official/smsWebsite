# Retry Strategy

## Policy

- Max retries: 3
- Backoff: exponential
- Jitter: enabled

---

## Example

```
Attempt 1 → wait 200ms
Attempt 2 → wait 500ms
Attempt 3 → fail
```

---

## Rules

- Retry only retryable errors
- Never retry payment/order finalization steps