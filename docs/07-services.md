# Services

This document describes the responsibilities of each microservice in the smsWebsite platform.

---

# API Gateway

## Responsibilities

- Single entry point for clients
- Authentication and authorization
- Request routing
- Rate limiting
- API versioning

Does **not** contain business logic.

---

# Auth Service

## Responsibilities

- Integrate with Auth0
- Manage user profiles
- Role-Based Access Control (RBAC)
- Permission management

Does **not** authenticate providers.

---

# Catalog Service

## Responsibilities

- Maintain product metadata
- Expose catalog APIs
- Return available Offers for products

Does **not**:

- Calculate prices
- Execute orders
- Communicate directly with providers

---

# Offer Engine Service

## Responsibilities

- Collect provider data
- Normalize provider responses
- Build Offers
- Apply currency conversion
- Apply configurable margins
- Apply discounts
- Calculate quality scores
- Rank Offers

Does **not**:

- Select the final Offer
- Execute orders
- Reserve wallet balance

---

# Order Service

## Responsibilities

- Create orders
- Execute the selected Offer
- Manage the order lifecycle
- Coordinate with Wallet Service
- Communicate with Provider Plugins
- Publish domain events

Does **not**:

- Calculate Offer prices
- Rank Offers

---

# Wallet Service

## Responsibilities

- Manage user balances
- Reserve funds
- Process deposits
- Process refunds
- Maintain transaction history

---

# SMS Service

## Responsibilities

- Receive SMS messages from providers
- Store received messages
- Expose SMS retrieval APIs
- Track SMS delivery status

---

# Scheduler Service

## Responsibilities

- Schedule synchronization jobs
- Trigger provider catalog updates
- Execute background maintenance tasks
- Retry scheduled operations

---

# Provider Plugin Layer

The Provider Plugin Layer is not a standalone microservice.

It is an internal integration layer responsible for:

- Communicating with external provider APIs
- Mapping provider-specific responses
- Isolating provider implementations
- Providing a unified interface to the Offer Engine and Order Service

Providers remain completely hidden from clients.

---

# Service Communication

Services communicate through:

- REST APIs (synchronous)
- RabbitMQ domain events (asynchronous)

Each service owns:

- its own database
- its own business logic
- its own API

No database is shared between services.

---

# Architecture Rules

- Users interact only with Offers.
- Providers are internal implementation details.
- Only the user selects the final Offer.
- Order Service executes the selected Offer without modifying it.
- Business capabilities are isolated within their owning service.