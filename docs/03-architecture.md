# Architecture

## Core Principle

smsWebsite is built on an **Offer-Based Architecture**.

Providers are considered internal infrastructure and are never exposed to clients.

Users interact only with **Offers**, while the system is responsible for executing the selected Offer through the appropriate provider.

---

## High-Level Architecture

```mermaid
flowchart LR

    User[User]

    Gateway[API Gateway]

    Catalog[Catalog Service]

    OfferEngine[Offer Engine]

    Order[Order Service]

    Wallet[Wallet Service]

    Plugins[Provider Plugin Layer]

    Providers[External SMS Providers]

    User --> Gateway

    Gateway --> Catalog

    Catalog --> OfferEngine

    OfferEngine --> Catalog

    Catalog --> User

    User -->|Select Offer| Gateway

    Gateway --> Order

    Order --> Wallet

    Order --> Plugins

    Plugins --> Providers
```

---

## Order Execution Flow

```mermaid
sequenceDiagram

    actor User

    participant Catalog as Catalog Service
    participant Offer as Offer Engine
    participant Order as Order Service
    participant Wallet as Wallet Service
    participant Plugin as Provider Plugin

    User->>Catalog: Request Offers

    Catalog->>Offer: Build Offers

    Offer-->>Catalog: Offer List

    Catalog-->>User: Display Offers

    User->>Order: Create Order (offer_id)

    Order->>Wallet: Reserve Balance

    Wallet-->>Order: Reserved

    Order->>Plugin: Execute Offer

    Plugin-->>Order: Activation Result
```

---

# Responsibility Boundaries

## Catalog Service

Responsible for:

- Managing product metadata
- Returning available Offers
- Serving catalog APIs

Does **not**:

- Communicate directly with providers
- Execute orders
- Apply pricing logic

---

## Offer Engine

Responsible for:

- Collecting provider data
- Normalizing responses
- Building Offers
- Calculating final Offer prices
- Applying margins
- Applying currency conversion
- Ranking Offers

Does **not**:

- Select the final Offer
- Create orders
- Reserve balances

---

## Order Service

Responsible for:

- Creating orders
- Managing order lifecycle
- Reserving wallet balance
- Executing selected Offers
- Receiving activation results

Does **not**:

- Calculate prices
- Rank Offers
- Know provider implementation details

---

## Provider Plugin Layer

Responsible for:

- Communicating with external provider APIs
- Mapping provider responses
- Hiding provider-specific implementations

Providers are **never exposed** outside this layer.

---

# Architecture Principles

- Offer-Based Architecture
- User-Driven Offer Selection
- Hidden Provider Model
- Event-Driven Communication
- Microservice Architecture
- Plugin-Based Provider Integration
- Database per Service
- API-First Design