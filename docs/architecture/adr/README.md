# Architecture Decision Records (ADRs)

> **One file per significant architectural decision.**
> Each ADR is also mirrored as a `[DECISION]` issue for discussion + searchability.

## Format

Filename: `NNNN-short-slug.md` (e.g. `0001-cosmos-db-for-ordering.md`)

Each ADR contains:
1. **Status** — Proposed / Accepted / Superseded by ADR-NNNN
2. **Context** — what forced the decision
3. **Decision** — what we chose
4. **Alternatives** — what we considered and rejected
5. **Consequences** — positive and negative
6. **Revisit trigger** — when to reopen

## Index

| ADR | Title | Status | Issue |
|---|---|---|---|
| [0001](0001-cosmos-db-for-ordering-sql-for-user.md) | Cosmos DB for Ordering, SQL for User | Accepted | – |
| [0002](0002-bff-for-collector-and-driver.md) | BFF pattern for Collector and Driver apps | Accepted | – |
| [0003](0003-immutable-audit-trail-user-ids.md) | Immutable audit trail — store IDs, resolve names at read time | Accepted | – |
| [0004](0004-route-owns-order-sequence.md) | Route owns order sequence via ordered `OrderIds` array | Accepted | – |
| [0005](0005-multitenancy-via-company-id-and-aad-groups.md) | Multi-tenancy via `CompanyId` + AAD group claims | Accepted | – |
