# Development Roadmap

This roadmap describes WHAT the team will build and in which order. Learning materials are intentionally kept outside this repository.

## Delivery model
- One-week Sprints during the early project stages.
- Detail only the current Sprint and the next one; keep later work at milestone/epic level.
- One Issue -> one focused branch -> implementation + tests -> Pull Request -> partner review -> CI -> merge.
- Both contributors implement features and tests. Rotate ownership; do not permanently split developer/tester roles.

## Phase 0 - Repository & Team Setup
Goal: create a safe, repeatable collaboration workflow.
Deliverables: shared repository, collaborators, Project board, labels, milestones, branch protection, Issue/PR templates, first reviewed PR from each contributor.

## Phase 1 - Backend Foundation
Goal: establish the Spring Boot application and development conventions.
Deliverables: application bootstrap, Maven build, package/module structure, environment configuration, PostgreSQL connectivity, Flyway baseline, centralized error model, logging conventions, health/readiness basics.

## Phase 2 - Catalog & Inventory
Goal: support the store catalog with reliable persistence and validation.
Features: Category, Product, Inventory, product CRUD, validation, pagination, sorting, filtering and search.
Quality: unit/integration/API tests for catalog rules and persistence.

## Phase 3 - Users & Security
Goal: authenticate users and enforce permissions.
Features: User, Role, registration, login, password hashing, JWT, RBAC, ownership checks, Customer/Admin access boundaries.
Quality: authentication, authorization and negative security tests.

## Phase 4 - Commerce Core
Goal: implement the core purchase flow with server-authoritative business logic.
Features: Cart, CartItem, inventory validation, coupons, checkout, Order and OrderItem.
Rules: positive quantities, quantity <= stock, server-side price calculation, purchase-price snapshot, coupon validity, minimum/usage rules, transaction-safe checkout.

## Phase 5 - Orders & Reliability
Goal: make commerce behavior robust under state changes and concurrent use.
Features: order history, order status transitions, cancellation policy, stock restoration, transaction boundaries, concurrency controls and no-overselling behavior.

## Phase 6 - Quality & Test Automation
Goal: build confidence across the application.
Coverage: JUnit 5, Mockito, AssertJ, Spring Boot Test, MockMvc and/or REST Assured, Testcontainers, regression suite, boundary/negative cases, JaCoCo evidence and bug workflow.

## Phase 7 - Demo Frontend & E2E
Goal: provide enough UI for demonstration and end-to-end verification.
Features: minimal customer/admin flows required for demo.
E2E journeys: login -> browse/search -> cart -> checkout -> order history; selected admin catalog/order flows. Use Playwright.

## Phase 8 - Containerization & DevOps
Goal: make the application reproducible and automate delivery checks.
Deliverables: Docker image, Docker Compose for app + PostgreSQL, environment/secrets handling, GitHub Actions build/test pipeline, automated quality gates, deployment pipeline structure.

## Phase 9 - AWS Deployment
Goal: deploy a secure, maintainable demo environment.
Choose AWS services at implementation time based on current cost, free-tier availability, simplicity and portfolio value. Document deployment architecture, configuration, secrets, logs and operational checks.

## Phase 10 - AI/RAG Store Assistant
Goal: add a bounded AI feature after the deterministic commerce system is stable.
Scope: product information, policies and FAQs using retrieval/RAG. The AI must not be authoritative for prices, stock, payments, checkout or order-state changes. Add retrieval/AI evaluation tests.

## Phase 11 - Portfolio Release
Goal: make engineering evidence easy to inspect.
Deliverables: polished README, architecture diagram, ERD, API documentation, test evidence, CI/CD evidence, deployed demo, AI/RAG explanation, screenshots/demo material, release notes and clean GitHub history.

## Release principle
A phase is complete only when its acceptance criteria are met, required tests pass, documentation is updated where needed, review is complete, and work is merged through the agreed GitHub workflow.
