# 03 - User Stories

## US-01 Register
As a visitor, I want to create a customer account so that I can place orders.

Acceptance criteria:
- Valid unique account data creates the account.
- Duplicate identity fields governed by the design are rejected.
- Password is hashed.
- Client cannot choose an Admin role during public registration.

## US-02 Browse products
As a customer, I want to browse active products so that I can decide what to buy.

Acceptance criteria:
- Inactive products are not returned in normal customer catalog results.
- Pagination has predictable defaults and limits.
- Sorting/filtering parameters are validated.

## US-03 Manage cart
As a customer, I want to add/update/remove cart items.

Acceptance criteria:
- Quantity must be positive.
- Cart belongs to authenticated customer.
- Customer cannot manipulate another customer's cart.
- Server controls product identity and current price source.

## US-04 Checkout
As a customer, I want to checkout my cart so that an order is created.

Acceptance criteria:
- Empty cart cannot checkout.
- All products are valid and purchasable.
- Stock is sufficient.
- Coupon is revalidated.
- Totals are calculated server-side.
- Order and stock changes succeed or fail together.
- Concurrent checkout does not oversell.

## US-05 View orders
As a customer, I want to see my order history.

Acceptance criteria:
- Only own orders are visible.
- Historical item price remains the purchase-time price.

## US-06 Cancel order
As a customer, I want to cancel an eligible order.

Acceptance criteria:
- Only cancellable statuses can be cancelled.
- Authorization is enforced.
- Stock restoration follows the documented policy.
- Repeated cancellation is safe/rejected consistently.

## US-07 Admin catalog
As an Admin, I want to manage products/categories/inventory.

Acceptance criteria:
- Customer role receives forbidden response.
- Validation and uniqueness rules apply.
- Destructive actions prefer deactivate/soft business behavior where history requires preservation.
