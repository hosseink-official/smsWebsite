# Rate Limiting

## Strategy

Each provider must define:

- requests per second
- burst limit
- cooldown time

---

## Example

```text
5 requests/sec
burst: 10
cooldown: 1s
```

---

## Handling

- Gateway must respect limits
- Retry after backoff on limit errors