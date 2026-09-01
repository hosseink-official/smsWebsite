# Glossary

This document defines the core terms used throughout the smsWebsite project.

---

# Product

A Product represents an SMS activation service offered by the platform.

Examples:

- Telegram
- WhatsApp
- Discord
- Google

A Product contains general information and may have multiple Offers.

---

# Offer

An Offer is a purchasable option for a Product.

Each Offer contains:

- price
- currency
- quality score
- availability
- estimated delivery information

Users select Offers, not Providers.

---

# Provider

A Provider is an external SMS activation platform (e.g. 5SIM, SMS-Man).

Providers are considered internal infrastructure and are never exposed to users or public APIs.

---

# Catalog

The Catalog is the read-only marketplace exposed to clients.

It contains:

- Products
- Countries
- Services
- Available Offers

The Catalog never exposes provider-specific information.

---

# Order

An Order represents a user's purchase of a selected Offer.

Each Order references exactly one Offer.

---

# Activation

An Activation is the lifecycle of a purchased phone number.

Typical states include:

- Created
- WaitingForSMS
- SMSReceived
- Completed
- Expired
- Cancelled

---

# Provider Plugin

A Provider Plugin is an isolated integration module responsible for communicating with a specific external Provider.

Its responsibilities include:

- API communication
- Authentication
- Response normalization
- Error mapping

---

# Offer Engine

The Offer Engine is responsible for generating Offers from provider data.

Responsibilities include:

- data normalization
- currency conversion
- margin calculation
- quality scoring
- Offer generation
- Offer ranking

The Offer Engine never selects the final Offer.

---

# Event

An Event is an immutable message describing a completed business action.

Examples include:

- OrderCreated
- OfferExecuted
- WalletDebited
- SMSReceived

Events are exchanged asynchronously through RabbitMQ.

---

# Domain Event

A Domain Event represents a meaningful change in the business domain.

Events are:

- immutable
- versioned
- idempotent
- traceable

---

# Correlation ID

A Correlation ID is a unique identifier used to trace a request across multiple services and events.

It enables end-to-end observability in a distributed system.

# Marketplace

The Marketplace is the public-facing platform that exposes Products and their available Offers to users.

It provides a unified experience regardless of the underlying Providers.