## Entity Relationship

```mermaid
erDiagram

    PRODUCTS ||--o{ OFFERS : has

    PRODUCTS {
        uuid id PK
        string country_code
        string country_name
        string service_code
        string service_name
        boolean active
        datetime created_at
        datetime updated_at
    }

    OFFERS {
        uuid id PK
        uuid product_id FK
        decimal price
        string currency
        int stock
        decimal quality_score
        string status
        datetime last_synced_at
        datetime created_at
        datetime updated_at
    }
```