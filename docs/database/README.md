# Database Design Overview

This folder contains all database schemas, ERD diagrams, and data flow designs.

---

## Databases

- Auth DB → Users & roles
- Catalog DB → Products & offers
- Order DB → Offer lifecycle execution
- Wallet DB → Payments & transactions

---

## Overall Database Relationship

![overal DB](ChatGPT%20Image%20Jun%2030,%202026,%2001_30_52%20PM.png)

```mermaid
flowchart LR

    AUTH[(Auth DB)]
    CATALOG[(Catalog DB)]
    ORDER[(Order DB)]
    WALLET[(Wallet DB)]

    AUTH -->|user_id| ORDER
    AUTH -->|user_id| WALLET

    CATALOG -->|offer_id| ORDER

    ORDER -->|order_id| WALLET
    ORDER -->|order lifecycle events| WALLET

    CATALOG -->|products + offers| ORDER
```

---

## Includes

- ERD diagrams (Mermaid)
- Data flow models
- Indexing strategy

---

## Key Idea

- Auth DB handles identity & roles
- Catalog DB handles products + offers
- Order DB executes offers only
- Wallet DB handles financial transactions

All cross-database relations are handled via **IDs + services**, not foreign keys.