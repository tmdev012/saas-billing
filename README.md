# SaaS Billing

> Production-ready subscription billing — Stripe integration, usage metering, invoice generation, dunning, webhook handlers. Drop-in payment infrastructure for any SaaS.

[![Python](https://img.shields.io/badge/python-3.10+-blue)]()
[![Stripe](https://img.shields.io/badge/Stripe-integrated-blueviolet)]()
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green)]()

## Architecture

```
Customer ──▶ Stripe Checkout ──▶ Webhook ──▶ DB Update
                                    │
                                    ▼
                              ┌───────────┐
                              │  Invoice   │──▶ Email
                              │ Generator  │
                              └───────────┘
                                    │
                                    ▼
                              ┌───────────┐
                              │  Dunning   │──▶ Retry failed payments
                              │  Engine    │──▶ Grace period
                              └───────────┘    ──▶ Suspension
```

## Pricing Tiers

| Tier | Price | Limits | Features |
|------|-------|--------|----------|
| Free | R0/mo | 100 queries/day | Local AI only |
| Pro | R99/mo | 10K queries/day | Cloud AI + priority support |
| Enterprise | R999/mo | Unlimited | Custom models + SLA + dedicated support |

## Webhook Events

| Event | Action |
|-------|--------|
| `checkout.session.completed` | Create subscription, provision access |
| `invoice.paid` | Update billing status, send receipt |
| `invoice.payment_failed` | Enter dunning flow, notify customer |
| `customer.subscription.deleted` | Revoke access, archive data |

## Revenue

This IS the revenue engine. Every SaaS product needs billing. **Use internally or license to other startups at R5,000 setup + R500/month.**

---
*MIT License*
