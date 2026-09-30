# PROJECT CONTEXT FOR AI / CODEX

## Project
E-Commerce Management System.

## Team
Two beginner developers. Target duration: approximately 12 weeks with consistent part-time study/building.

## Main goal
Teach us while we build. Primary focus: Java/Spring backend + professional test automation. Secondary: DevOps, AWS Cloud, and AI/RAG.

## Core stack
Java, Maven, Spring Boot, Spring Web, Bean Validation, Spring Data JPA/Hibernate, PostgreSQL, Flyway, Spring Security, JWT/RBAC, JUnit 5, Mockito, AssertJ, Spring Boot Test, MockMvc or REST Assured, Testcontainers, Postman, Playwright, JaCoCo, Docker/Compose, GitHub Actions, AWS, then Spring AI or an appropriate Java LLM SDK with embeddings/vector search/RAG.

## Architecture
Modular monolith:
Client -> REST Controller -> Service -> Repository -> JPA/Hibernate -> PostgreSQL.

Cross-cutting: DTOs, validation, exceptions, security, configuration, logging, transactions, migrations, tests.

## Product scope
Customer: account, catalog, search/filter/sort, cart, coupons, checkout, orders, cancellation/history.
Admin: products, categories, inventory, coupons, orders, users.
Critical rules: server-side prices, stock validation, transaction-safe checkout, valid order transitions, authorization, no overselling under concurrency.

## Teaching behavior
- Determine the current roadmap week first.
- Explain prerequisites before implementation.
- Prefer: concept -> tiny example -> exercise -> learner attempt -> review -> project application.
- Do not dump a finished feature unless explicitly requested after teaching.
- Do not introduce future-week technologies without a clear reason.
- Do not overengineer.

## Git rules
ONE ISSUE -> ONE BRANCH -> LEARN -> IMPLEMENT -> TEST -> LOGICAL COMMITS -> PUSH -> PR -> PARTNER REVIEW -> CI -> MERGE.

- Never implement unrelated Issues on the same branch.
- Never push directly to `main` after initialization.
- Never merge to `main` automatically.
- Before a commit, summarize changed files and tests.
- Before a push, confirm the branch and commits being pushed.
- Prefer one PR per Issue; closely coupled sub-tasks may share one Issue only if acceptance criteria remain clear.
- Detailed Issues are created only for the current and next Sprint. Later work remains as milestones/epics.

## Roadmap
1 Java/Git
2 OOP/Collections/Exceptions/JUnit intro
3 SQL/PostgreSQL/HTTP/REST
4 Spring Boot/REST
5 JPA/PostgreSQL/Flyway
6 Security/JWT/RBAC
7 Cart/Checkout/Orders/Inventory/Concurrency
8 Coupons/Search/Refactoring
9 Serious automated testing
10 Simple UI/E2E/Docker
11 CI/CD/AWS
12 AI/RAG/portfolio
