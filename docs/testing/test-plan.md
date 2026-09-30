# Test Plan

## Scope
Authentication, catalog, cart, coupons, checkout, inventory, orders, authorization, persistence, API contracts, E2E critical flows.

## Types
Unit, integration, API, database, security/negative, concurrency, smoke, regression, E2E.

## Environments
- unit: no external database where not needed
- integration: disposable PostgreSQL Testcontainer
- E2E: containerized/local test environment
- cloud smoke: deployed environment with safe test data

## Entry criteria
Feature acceptance criteria understood; test data/preconditions known.

## Exit criteria
Critical acceptance tests pass; no known critical defect; CI green; required documentation updated.

## Risks
Flaky E2E, shared test state, time-dependent coupon tests, concurrency nondeterminism, environment differences. Mitigate with deterministic test data, isolated containers, controlled clocks where learned/needed, and narrow E2E scope.
