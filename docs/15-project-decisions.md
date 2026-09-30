# 15 - Architecture Decision Log

Use this file to record important decisions and alternatives.

## ADR-001 Modular monolith
Decision: start as a modular monolith.
Why: simpler learning/deployment/testing; domain does not require distributed systems.
Rejected for v1: microservices.

## ADR-002 PostgreSQL
Decision: relational database.
Why: orders, users, products, inventory and transactions benefit from relational constraints and transactions.

## ADR-003 BigDecimal for money
Decision: use BigDecimal for monetary business calculations.
Why: avoid binary floating-point rounding behavior for money.

## ADR-004 OrderItem price snapshot
Decision: store purchase-time price in OrderItem.
Why: historical orders must not change when catalog price changes.

## ADR-005 Testcontainers
Decision: use disposable PostgreSQL containers for important integration tests.
Why: test behavior against a real database engine with reproducible setup.

## ADR-006 AI after core
Decision: RAG assistant is added after deterministic store functions.
Why: AI should enrich the product, not replace secure transaction logic.

## Future ADR
Document the chosen concurrency/locking strategy for inventory and why it was selected.
