# Enterprise Automation Architecture — 30+ Production Workflows

A Product Manager portfolio project demonstrating how I designed and deployed 30+ production automations for a 500,000+ subscriber telecom partner ecosystem across 19 directories.

## Live Demo

[View the interactive demo](https://sangythek190.github.io/enterprise-automation-architecture/)

## What This Demonstrates

- **Operational Scale** — 30+ automations across 6 categories (Order Processing, Fulfillment, Contract Billing Sync, Product Management, Retention, Onboarding) running in production
- **Order Lifecycle Simulation** — Interactive click-through of a complete order: sales submission, credit vetting (TransUnion), approve/decline branching, fulfillment auto-kick, billing sync, and retention handling
- **Decision Tree Design** — Branching automations for credit check outcomes, payment failures, and order cancellations
- **Self-Healing Patterns** — Automations that detect product activation failures and auto-recover without support escalation
- **Billing Reconciliation** — Audit automation that catches drift between platform and Contract Billing before it becomes revenue leakage

## Automation Categories

| Category | Count | What It Does |
|----------|-------|-------------|
| Order Processing | 12 | Submit, validate, credit vet, approve/decline, cancel |
| Fulfillment | 8 | Auto-kick projects for 8 product types on activation |
| Contract Billing Sync | 5 | Two-way sync, audit, push contracts and customer info |
| Product Management | 3 | Activation, self-healing, timed deactivation |
| Retention | 2 | Cancellation notification + 2-day SLA sales task |
| Onboarding & Identity | 3 | Welcome, subscriber ID assignment, deactivation webhooks |

## Architecture

```
Sales Submits Order
        |
        v
   [Credit Vetting — TransUnion]
        |
   ┌────┴────┐
   v         v
 Approve   Decline
   |         └──> Notify Sales Rep + Create Task
   v
 [CPE Processing]
   |
   v
 [Fulfillment — 8 product automations]
   |
   v
 [Contract Billing Sync + Audit]
   |
   v
 Product Live ──> Payment Fails? ──> Auto-Cancel + Retention (2-day SLA)
```

## Author

**Sangeetha K** — Product Manager, Integrations & Professional Services

## License

MIT
