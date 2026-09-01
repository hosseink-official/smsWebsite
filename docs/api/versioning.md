# API Versioning Strategy

## Version Format

All APIs follow:

```
/api/v1/
/api/v2/
```

---

## Rules

- Breaking changes → new version
- No silent changes allowed
- Old versions supported for minimum 6 months

---

## Deprecation Policy

1. Mark endpoint as deprecated
2. Log usage
3. Remove after migration window