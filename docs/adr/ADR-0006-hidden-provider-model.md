# ADR-0006: Hidden Provider Model (Abstract Offer Marketplace)

## Status
Accepted

---

## Context

The system aggregates SMS activation services from multiple external providers. Each provider offers:

- Different pricing
- Different availability
- Different reliability
- Different speed characteristics

Initially, providers were considered part of the user-facing model, where each offer would be associated with a specific provider.

However, exposing provider identity introduces several issues:

- User bias toward known providers
- Competitive manipulation between providers
- Reduced flexibility in backend provider switching
- Increased coupling between UI and provider layer

---

## Decision

We will adopt a **Hidden Provider Model**, where:

- Providers are **not exposed to end users**
- Users only see **abstracted offers**
- Each offer is represented as a normalized option containing:
  - price
  - quality attributes (speed, reliability, stock status)
  - internal option identifier

Providers will only exist in the internal system layer.

---

## Offer Model (Public API)

Each product will expose multiple offers:

```json
{
  "product": "Telegram UK",
  "offers": [
    {
      "id": "opt_1",
      "price": 0.75,
      "label": "Fast",
      "reliability": "medium"
    },
    {
      "id": "opt_2",
      "price": 0.80,
      "label": "High Success Rate",
      "reliability": "high"
    }
  ]
}
```

No provider identifiers are exposed in the public API.

Internal Mapping (Hidden Layer)

Internally, each offer maps to a provider:

Provider A → opt_1
Provider B → opt_2

This mapping is only used within the Aggregator Service and is not exposed externally.

Consequences
Positive
Increased system flexibility
Ability to switch providers without frontend changes
Reduced provider-driven bias
Cleaner marketplace abstraction
Improved UX consistency
Negative
Reduced transparency of supply chain
Harder for advanced users to optimize provider selection
Requires strong internal scoring/labeling system
Increased responsibility on Aggregator service
Alternatives Considered
1. Expose Provider Names

Rejected due to:

UI bias
coupling frontend to provider identity
reduced abstraction
2. Fully Transparent Marketplace

Rejected due to:

complexity overload
poor UX for non-technical users
Notes

This decision strongly couples with:

Aggregator scoring engine
Offer labeling system
Pricing normalization layer

Future ADRs may refine:

Offer scoring weights
Label generation strategy
Provider reliability scoring

---
