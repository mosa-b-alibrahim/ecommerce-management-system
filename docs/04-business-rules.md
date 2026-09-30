# 04 - Business Rules

Each important rule receives an ID so requirements and tests can reference it.

## Money
- BR-MONEY-01: Use decimal-safe money representation (`BigDecimal` in Java), not floating-point `double`, for business money calculations.
- BR-MONEY-02: Backend is authoritative for prices and totals.
- BR-MONEY-03: `OrderItem` stores a purchase-time price snapshot; changing Product price later must not alter historical orders.

## Products
- BR-PROD-01: Only active/purchasable products can be added to a normal customer cart.
- BR-PROD-02: SKU is unique if SKU is part of the final model.
- BR-PROD-03: Price cannot be negative.

## Cart
- BR-CART-01: Quantity must be >= 1.
- BR-CART-02: A customer can access only their own cart.
- BR-CART-03: Cart is not an order; availability and price are revalidated at checkout.

## Coupons
- BR-COUPON-01: Coupon must be active and inside its validity window.
- BR-COUPON-02: Minimum order amount is checked against the documented subtotal definition.
- BR-COUPON-03: Coupon stacking is disabled in v1 unless explicitly redesigned.
- BR-COUPON-04: Discount cannot create a negative final total.

## Checkout
1. Identify authenticated customer.
2. Load cart.
3. Reject empty cart.
4. Revalidate products.
5. Read authoritative prices.
6. Revalidate coupon.
7. Calculate subtotal/discount/final total.
8. Validate stock.
9. Create order + immutable order item snapshots.
10. Reduce stock.
11. Commit transaction.
12. Clear/adjust cart according to implementation decision.

- BR-CHK-01: Steps that change order/stock are transaction-safe.
- BR-CHK-02: Any failure before commit leaves no partial successful purchase.
- BR-CHK-03: Two concurrent buyers cannot both purchase the final unit.
- BR-CHK-04: The exact locking/consistency strategy is documented when implemented and proven by an integration/concurrency test.

## Orders
Suggested lifecycle to refine:
`CREATED -> CONFIRMED -> PROCESSING -> SHIPPED -> DELIVERED`
with eligible cancellation paths to `CANCELLED`.

- BR-ORD-01: Invalid transitions are rejected.
- BR-ORD-02: Delivered orders cannot be cancelled.
- BR-ORD-03: Customer may only act on own orders.
- BR-ORD-04: Cancellation stock restoration occurs exactly once when policy says stock should be restored.

## Example concurrency scenario
Stock = 1. Customer A and Customer B checkout concurrently.
Expected invariant: successful purchased quantity <= available stock. At most one request succeeds for that final unit.
