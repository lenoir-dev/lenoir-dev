# Go Backend Engineer | Distributed Systems & Reliability

## About

I build Go APIs and background services with attention to transactional integrity, asynchronous work, and failure recovery. These portfolio projects explore PostgreSQL-backed state, external integrations, and what happens when a worker, provider, or network fails between steps.

## Core Technologies

**Backend:** Go, REST APIs, PostgreSQL, SQL, Docker  
**Messaging and operations:** NATS JetStream, Redis, GitHub Actions, OpenTelemetry  
**Additional domain:** EVM infrastructure and Solidity

## Featured Projects

### [LenoirDesk](https://github.com/lenoir-dev/LenoirDesk)

Multi-tenant billing integration that turns Stripe events into durable HubSpot and Slack work. **Go, PostgreSQL, NATS JetStream, Redis.** A transactional inbox/outbox, fenced worker claims, and explicit handling of uncertain external effects show event-driven processing, state transitions, and recovery design.

### [Transaction-Orchestrator](https://github.com/lenoir-dev/Transaction-Orchestrator)

Go service that tracks an EVM transaction through submission, replacement, and confirmation. **Go, PostgreSQL, REST, EVM RPC.** Transactional nonce reservation, persisted signed attempts before broadcast, and receipt reconciliation show idempotency, transaction boundaries, and crash recovery.

### [ReorgGuard](https://github.com/lenoir-dev/ReorgGuard)

Event indexer that keeps a PostgreSQL view aligned with changing chain history. **Go, PostgreSQL, EVM RPC.** Concurrent range fetching with ordered commits, durable checkpoints, and atomic reorganization updates show concurrency control and consistent data projection.

## Blockchain Infrastructure

- [SettleKit](https://github.com/lenoir-dev/SettleKit) — payment intents, an ERC-20 escrow, canonical event indexing, and signed webhook delivery.
- [BridgeWatch](https://github.com/lenoir-dev/BridgeWatch) — independent chain watchers, durable checkpoints, and evidence-based message reconciliation.
- [Gasless-Policy-Engine](https://github.com/lenoir-dev/Gasless-Policy-Engine) — policy-based transaction sponsorship with PostgreSQL budget reservations and an ERC-4337 paymaster.

## Engineering Evidence

| Engineering skill | Repository | Implementation / Tests |
| --- | --- | --- |
| Worker lifecycle and state machines | LenoirDesk | [Action transitions](https://github.com/lenoir-dev/LenoirDesk/blob/main/internal/business/action_state.go) · [transition tests](https://github.com/lenoir-dev/LenoirDesk/blob/main/internal/business/action_state_test.go) |
| PostgreSQL transactions and idempotency | Transaction-Orchestrator | [Persistence](https://github.com/lenoir-dev/Transaction-Orchestrator/blob/main/internal/orchestrator/postgres.go) · [transaction tests](https://github.com/lenoir-dev/Transaction-Orchestrator/blob/main/internal/orchestrator/transaction_test.go) |
| Concurrency and ordered commits | ReorgGuard | [Parallel fetch](https://github.com/lenoir-dev/ReorgGuard/blob/main/internal/backfill/parallel.go) · [parallel tests](https://github.com/lenoir-dev/ReorgGuard/blob/main/internal/backfill/parallel_test.go) |
| Fault recovery | ReorgGuard | [Atomic reorg update](https://github.com/lenoir-dev/ReorgGuard/blob/main/internal/store/reorg.go) · [integration tests](https://github.com/lenoir-dev/ReorgGuard/blob/main/internal/store/reorg_integration_test.go) |
| Integration testing | LenoirDesk | [Business integration tests](https://github.com/lenoir-dev/LenoirDesk/blob/main/tests/integration/business_test.go) · [CI workflow](https://github.com/lenoir-dev/LenoirDesk/blob/main/.github/workflows/ci.yml) |

## Portfolio Notice

These are non-commercial engineering demonstrations. Local tests and benchmarks document reproducible behavior in their stated environments; they do not establish production operation or service-level performance.
