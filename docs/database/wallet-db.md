# Wallet Database

## Table: wallets

```sql
CREATE TABLE wallets (
    id UUID PRIMARY KEY,
    user_id VARCHAR(100),
    balance BIGINT,
    currency VARCHAR(10),
    updated_at TIMESTAMP
);
```

---

## Table: transactions

```sql
CREATE TABLE transactions (
    id UUID PRIMARY KEY,

    wallet_id UUID,

    type VARCHAR(30),

    amount BIGINT,

    reference_id VARCHAR(100),

    status VARCHAR(30),

    created_at TIMESTAMP
);
```

---

## Transaction Types

- DEPOSIT
- WITHDRAW
- PAYMENT
- REFUND