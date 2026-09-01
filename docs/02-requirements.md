# Requirements

## Functional Requirements

### Providers
- Integrate multiple SMS providers
- Support plugin-based architecture
- Normalize provider responses

---

### Catalog
- Aggregate all services from providers
- Show countries, services, prices
- Real-time stock updates

---

### Orders
- Create orders from catalog items
- Track order status
- Reserve numbers
- Fetch SMS messages

---

### Wallet
- User balance management
- Deposit / Withdraw
- Automatic refunds

---

### Pricing
- Convert USD → local currency
- Apply margins
- Apply discounts

---

### Authentication
- Auth0 integration
- Internal auth service
- Role-based access control

---

## Non-Functional Requirements

- High scalability (horizontal scaling)
- Event-driven architecture
- Fault tolerance
- Provider failure isolation
- Low latency catalog API
- Caching with Redis
- Observability (logs, metrics, tracing)

---

## Constraints

- No direct frontend access to providers
- No shared database between services
- Provider APIs are abstracted via plugins