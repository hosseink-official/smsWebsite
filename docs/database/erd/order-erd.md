## Entity Relationship

```mermaid
erDiagram

    ORDERS ||--o| ACTIVATIONS : has

    ORDERS {
        uuid id PK
        uuid user_id
        uuid offer_id
        string status
        bigint price_paid
        string currency
        datetime created_at
        datetime updated_at
    }

    ACTIVATIONS {
        uuid id PK
        uuid order_id FK
        string phone_number
        string sms_code
        string status
        datetime created_at
        datetime updated_at
    }
```