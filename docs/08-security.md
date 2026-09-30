# 08 - Security

## Concepts to learn
Authentication answers "Who are you?" Authorization answers "What may you do?"

## Planned controls
- Spring Security
- secure password hashing
- JWT-based API authentication
- CUSTOMER and ADMIN roles initially
- server-side role checks
- DTO validation
- secrets via environment/configuration, never committed

## Rules
- Public registration cannot create Admin accounts.
- Customer cannot call Admin catalog/inventory endpoints.
- Customer cannot read/modify another customer's cart/orders.
- Never trust price, total, role, or ownership supplied by client.
- Do not log passwords, tokens, secrets, or unnecessary personal data.
- JWT does not make data trustworthy by itself; authorization and business checks still happen server-side.
- Use HTTPS in deployed environments.

## Authentication flow
```mermaid
sequenceDiagram
    participant U as User
    participant API
    participant SEC as Spring Security
    participant DB
    U->>API: Login credentials
    API->>DB: Load user
    API->>SEC: Verify password
    SEC-->>API: Valid identity
    API-->>U: Access token
    U->>API: Request + Bearer token
    SEC->>SEC: Validate token/authorities
    API-->>U: Allowed response or 401/403
```

Exact JWT lifetime/refresh strategy is selected when Security is implemented, not invented prematurely.
