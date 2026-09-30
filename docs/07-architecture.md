# 07 - Architecture

## Style
Modular monolith. We intentionally avoid microservices in v1.

```mermaid
flowchart LR
    C[Client / Simple UI / Postman] --> API[Spring REST Controllers]
    API --> S[Services / Business Logic]
    S --> R[Repositories]
    R --> JPA[JPA / Hibernate]
    JPA --> DB[(PostgreSQL)]
    S --> SEC[Security / Authorization]
    S --> LOG[Logging]
```

## Request flow
```mermaid
sequenceDiagram
    participant Client
    participant Controller
    participant Service
    participant Repository
    participant DB
    Client->>Controller: HTTP request + token
    Controller->>Service: validated DTO / use case
    Service->>Repository: query/change data
    Repository->>DB: SQL via JPA/Hibernate
    DB-->>Repository: result
    Repository-->>Service: domain data
    Service-->>Controller: result
    Controller-->>Client: HTTP response
```

## Package direction
Suggested later:
- controller
- dto
- service
- repository
- entity
- security
- exception
- config

Do not create empty abstraction layers just to match a diagram. Introduce them when their responsibilities are understood.

## Checkout flow
```mermaid
flowchart TD
    A[Checkout request] --> B[Authenticate customer]
    B --> C[Load cart]
    C --> D{Cart empty?}
    D -- Yes --> X[Reject]
    D -- No --> E[Revalidate products/prices/coupon]
    E --> F[Validate stock]
    F --> G{Enough stock?}
    G -- No --> X
    G -- Yes --> H[Transaction: create order + items]
    H --> I[Reduce stock safely]
    I --> J[Commit]
    J --> K[Return order]
```

## Order lifecycle
```mermaid
stateDiagram-v2
    [*] --> CREATED
    CREATED --> CONFIRMED
    CREATED --> CANCELLED
    CONFIRMED --> PROCESSING
    CONFIRMED --> CANCELLED
    PROCESSING --> SHIPPED
    SHIPPED --> DELIVERED
```
The final allowed transitions are a business decision and must be tested.
