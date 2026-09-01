## Entity Relationship

```mermaid
erDiagram

    WALLETS ||--o{ TRANSACTIONS : contains

    WALLETS {
        uuid id PK
        uuid user_id
        bigint balance
        string currency
        datetime created_at
        datetime updated_at
    }

    TRANSACTIONS {
        uuid id PK
        uuid wallet_id FK
        uuid order_id
        string type
        bigint amount
        bigint balance_after
        string status
        string external_reference
        datetime created_at
        datetime updated_at
    }
```