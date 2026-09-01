# Event Flow

## System is fully event-driven

---

## Order Flow

```
OrderCreated
   ↓
ReserveProduct
   ↓
Call Provider
   ↓
OrderUpdated
   ↓
SMSReceived
   ↓
OrderCompleted
```

---

## Catalog Flow

```
ProviderSyncStarted
   ↓
ProductUpdated
   ↓
CatalogRebuilt
   ↓
CacheInvalidated
```

---

## Wallet Flow

```
WalletCharged
   ↓
OrderPaid
   ↓
WalletDebited
   ↓
RefundIssued (if failed)
```

---

## Rules

- Events are immutable
- Events are versioned
- Events are replayable