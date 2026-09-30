# 02 - Requirements

## Functional Requirements

### Authentication and users
- FR-AUTH-01: A visitor can register as a Customer.
- FR-AUTH-02: A registered user can log in.
- FR-AUTH-03: The API exposes the authenticated user's basic profile.
- FR-AUTH-04: Admin-only operations reject Customers.
- FR-AUTH-05: Passwords are never stored as plaintext.

### Catalog
- FR-CAT-01: Customers can list active products.
- FR-CAT-02: Customers can view a product by ID.
- FR-CAT-03: Products can be searched and filtered.
- FR-CAT-04: Product lists support pagination and sorting.
- FR-CAT-05: Admin can create/update/deactivate products.
- FR-CAT-06: Admin can manage categories.

### Cart
- FR-CART-01: Customer can add an active product to the cart.
- FR-CART-02: Customer can update quantity.
- FR-CART-03: Customer can remove an item.
- FR-CART-04: Cart totals displayed to the user are recalculated by the server.
- FR-CART-05: Invalid/non-positive quantities are rejected.

### Coupons
- FR-COUPON-01: Eligible coupon can reduce an order according to its rules.
- FR-COUPON-02: Expired/inactive coupon is rejected.
- FR-COUPON-03: Minimum-order requirements are enforced.
- FR-COUPON-04: Discount calculation cannot make the payable total negative.

### Checkout and inventory
- FR-CHK-01: Checkout validates products, prices, quantities, coupon, and stock.
- FR-CHK-02: Successful checkout creates an Order and OrderItems.
- FR-CHK-03: Successful checkout reduces stock atomically.
- FR-CHK-04: Failed checkout does not leave partial order/stock changes.
- FR-CHK-05: Concurrent checkout cannot oversell the same stock.

### Orders
- FR-ORD-01: Customer can view own orders.
- FR-ORD-02: Customer cannot view another customer's orders.
- FR-ORD-03: Admin can view/manage orders according to role.
- FR-ORD-04: Only valid status transitions are accepted.
- FR-ORD-05: Cancellation follows a documented policy and stock-restoration rule.

## Non-Functional Requirements
- NFR-01 Security: server-side authorization and validation.
- NFR-02 Reliability: checkout is transactional.
- NFR-03 Testability: business logic is structured so it can be unit/integration tested.
- NFR-04 Maintainability: clear modular-monolith boundaries and naming.
- NFR-05 Observability: useful logs without leaking secrets.
- NFR-06 Reproducibility: migrations and Docker setup recreate the environment.
- NFR-07 CI: pull requests run automated quality/test checks.
- NFR-08 Configuration: secrets and environment-specific values stay outside source code.
