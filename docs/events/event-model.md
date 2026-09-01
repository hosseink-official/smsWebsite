# Event Bus Design

smsWebsite uses RabbitMQ as a fully event-driven backbone for an Offer-Based Marketplace Architecture.

Providers are completely hidden and never appear in the event system.

---

# 🧠 Core Principles

- Events are immutable
- Events are versioned
- Events are domain-driven (Offer / Order / Wallet / Catalog / SMS)
- No provider exposure in any event
- At-least-once delivery model
- Consumers must be idempotent

---

# 🏗️ RabbitMQ Topology

## Main Exchange

### domain.exchange (topic)

All business events flow through this exchange.

Routing keys:

- offer.*
- order.*
- wallet.*
- catalog.*
- sms.*

---

## Retry Exchange

### event.retry.exchange

Used for retrying failed events with backoff strategy.

---

## Dead Letter Exchange (DLQ)

### event.dlq.exchange

Stores failed events that cannot be processed.

Used for debugging and manual replay.

---

# 📦 Queue Design

## Order Service Queues

- order.created.queue
- order.processing.queue
- order.completed.queue
- order.failed.queue

Binding:


order.*


---

## Offer Engine Queues

- offer.build.queue
- offer.refresh.queue

Binding:


offer.*


---

## Wallet Service Queues

- wallet.credit.queue
- wallet.debit.queue
- wallet.refund.queue

Binding:


wallet.*


---

## Catalog Service Queues

- catalog.update.queue

Binding:


catalog.*


---

## SMS / Activation Service Queues

- sms.incoming.queue
- sms.delivery.queue

Binding:


sms.*


---

# 🔁 Retry Strategy

## Retry Flow

1. Event fails processing
2. Event sent to retry.exchange
3. Backoff delay applied
4. Retry attempted again
5. After max retries → DLQ

---

## Retry Backoff Table

| Attempt | Delay |
|--------|------|
| 1 | 5 seconds |
| 2 | 30 seconds |
| 3 | 2 minutes |
| 4 | 10 minutes |

---

# ☠️ Dead Letter Queue (DLQ)

All failed events go to:


event.dlq.exchange


Used for:

- debugging
- replay
- monitoring system health

---

# 🧠 Event Contract

## Base Event Structure

```json
{
  "event": "string",
  "version": "1.0",
  "event_id": "uuid",
  "timestamp": "ISO-8601",
  "correlation_id": "uuid",
  "payload": {}
}