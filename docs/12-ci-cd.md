# 12 - CI/CD

## Target PR pipeline
```mermaid
flowchart LR
    PR[Pull Request] --> B[Build]
    B --> U[Unit Tests]
    U --> I[Integration/API Tests]
    I --> C[Coverage/Quality]
    C --> D[Docker Build]
    D --> E[E2E when stable]
    E --> OK[Merge eligible]
```

## Principles
- Add stages incrementally as the corresponding testing/tooling is learned.
- A failing critical test blocks merge.
- Do not create a fake complicated pipeline for portfolio appearance.
- Cache dependencies only after baseline pipeline works.
- Deployment secrets use GitHub/AWS secret mechanisms, never repository files.

## CD
Cloud deployment automation is added only after a manual/simple deployment is understood. Production-like deployment should be reproducible and documented.
