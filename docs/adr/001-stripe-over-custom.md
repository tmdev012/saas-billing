# ADR-001: Stripe Over Custom Payment Processing

## Status: Accepted | Date: 2026-02-10

## Decision
Use Stripe for all payment processing rather than building custom.

## Why
- Stripe handles PCI compliance (massive liability otherwise)
- Built-in tax calculation, invoicing, dunning
- Webhook-driven = clean event architecture
- 2.9% + R5 per transaction is cheaper than building + maintaining + auditing custom payments
