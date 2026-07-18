# Billing Status Propagation Architecture Spec

## Problem Statement

Billing currently lives inside the monolith, but other services need near-real-time invoice status. The design must expose status changes without creating inconsistent invoice state or forcing a risky service extraction.

## Context

- Billing writes remain owned by the monolith.
- Consumers need read access, not direct mutation rights.
- Status propagation must tolerate retries and partial outages.

## Recommended Design

Use a transactional outbox in the monolith to publish invoice status events. Downstream services consume events into local read models. Keep billing write ownership in the monolith until event contracts and operational behavior are stable.

## Interface Contract

- Event: `InvoiceStatusChanged`
- Key fields: `invoice_id`, `account_id`, `old_status`, `new_status`, `version`, `occurred_at`
- Delivery: at-least-once
- Consumer requirement: idempotent processing by `invoice_id` and `version`

## Data Flow

1. Billing transaction updates invoice status.
2. Same transaction inserts an outbox row.
3. Outbox publisher emits the event.
4. Consumers update local read models if the event version is newer.
5. Monitoring checks outbox lag and consumer freshness.

## Rejected Alternatives

- Immediate service extraction: too much migration risk for a read propagation need.
- Direct cross-service reads from monolith database: couples consumers to billing schema and creates scaling risk.
- Synchronous callbacks: fragile under consumer outage and increases billing latency.

## Failure Modes

- Duplicate events: handled by versioned idempotency.
- Publisher outage: outbox lag alert and replay.
- Consumer lag: freshness metric and degraded UI state.

## Verification Criteria

- Integration test: status update creates exactly one logical event.
- Replay test: duplicate events do not regress status.
- Outage test: publisher can resume from outbox without data loss.

## Open Risks / TODO

- TODO: define retention and replay window for outbox rows.
- TODO: choose schema evolution policy for event fields.
