# 06 - API Design

This is a planning contract. Exact payloads are refined after HTTP/Spring lessons.

## Authentication
- `POST /api/v1/auth/register`
- `POST /api/v1/auth/login`
- `GET /api/v1/users/me`

## Catalog
- `GET /api/v1/products`
- `GET /api/v1/products/{id}`
- `POST /api/v1/products` - Admin
- `PATCH /api/v1/products/{id}` - Admin
- `GET /api/v1/categories`
- Admin category endpoints as required.

## Cart
- `GET /api/v1/cart`
- `POST /api/v1/cart/items`
- `PATCH /api/v1/cart/items/{itemId}`
- `DELETE /api/v1/cart/items/{itemId}`

## Checkout / Orders
- `POST /api/v1/checkout`
- `GET /api/v1/orders`
- `GET /api/v1/orders/{id}`
- `POST /api/v1/orders/{id}/cancel`

## Coupons/Admin inventory
Endpoints are added after the domain model is finalized.

## Status code guidance
- 200: successful read/update/action where appropriate
- 201: resource created
- 400: malformed/business-invalid request where chosen by API policy
- 401: not authenticated
- 403: authenticated but forbidden
- 404: resource not found or intentionally hidden
- 409: state/resource conflict such as duplicate/stock conflict where appropriate
- 500: unexpected server failure

Spring validation may produce framework-specific validation behavior; document the final error contract rather than copying status-code rules blindly.

## Error response goal
Use one consistent shape, for example:
- timestamp/request correlation if adopted
- status
- stable error code
- human-readable message
- field validation details when relevant
Never leak stack traces or secrets to clients.
