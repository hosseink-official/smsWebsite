# Database Indexing Strategy

## Auth DB

- users.email (unique index)
- user_roles.user_id

---

## Catalog DB

- provider_products.provider_id
- provider_products.product_id
- products.type

---

## Order DB

- orders.user_id
- orders.status
- orders.provider_id
- activations.order_id

---

## Wallet DB

- transactions.wallet_id
- transactions.type
- wallets.user_id

---

## Rules

- Index all foreign keys
- Optimize for read-heavy catalog queries
- Avoid over-indexing write-heavy tables