# Provider SDK Versioning

## Principle

Provider SDK evolves independently from core system.

---

## Version Strategy

```
v1 → stable interface
v2 → breaking changes (new interface)
```

---

## Rules

- Providers must declare supported SDK version
- Multiple versions may run in parallel
- Core system must support backward compatibility

---

## Compatibility Rule

- Minor changes = backward compatible
- Major changes = new interface version