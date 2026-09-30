# 01 - Project Overview

## Why this project?
A serious store backend contains more than CRUD. It creates opportunities to learn authentication, authorization, relational modeling, transactions, concurrency, validation, testing, deployment, and AI integration in one understandable domain.

## Actors
### Customer
Creates an account, signs in, browses products, searches/filters/sorts, manages a cart, applies eligible coupons, checks out, views orders, and cancels orders when policy permits.

### Admin
Manages products, categories, stock, coupons, orders, users, and product availability.

## v1 boundaries
Included: catalog, cart, checkout, inventory, orders, coupons, security, testing, DevOps/cloud, scoped AI assistant.

Not included initially: marketplace/multiple sellers, storing real card details, complex payment gateway integration, microservices, Kafka, Kubernetes, Terraform, advanced recommendation engine, advanced frontend.

## Success criteria
The final repository should demonstrate:
- understandable Java/Spring code,
- explicit business rules,
- safe database behavior,
- meaningful automated tests,
- real two-person Git history,
- Dockerized local setup,
- CI pipeline,
- cloud deployment,
- documented architecture,
- AI/RAG feature that is separated from deterministic checkout logic.
