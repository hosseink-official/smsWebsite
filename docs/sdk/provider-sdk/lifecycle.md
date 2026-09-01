# Provider Lifecycle

## States

```
INIT → READY → RUNNING → STOPPED → FAILED
```

---

## Hooks

```go
Initialize()
HealthCheck()
Shutdown()
```

---

## Rules

- Providers must be safely restartable
- No persistent state inside plugin memory