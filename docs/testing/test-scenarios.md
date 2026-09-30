# Test Scenarios

- TS-AUTH-01 Valid registration/login
- TS-AUTH-02 Duplicate/invalid registration
- TS-SEC-01 Customer attempts Admin endpoint
- TS-SEC-02 Customer attempts another customer's order
- TS-PROD-01 Browse active products
- TS-PROD-02 Search/filter/pagination
- TS-CART-01 Add/update/remove item
- TS-CART-02 Invalid quantity/inactive product
- TS-COUPON-01 Valid coupon
- TS-COUPON-02 Expired/inactive/minimum-not-met coupon
- TS-CHK-01 Successful checkout
- TS-CHK-02 Empty cart
- TS-CHK-03 Insufficient stock
- TS-CHK-04 Failure rolls back order/stock changes
- TS-CHK-05 Two concurrent customers target final unit
- TS-ORD-01 Customer order history
- TS-ORD-02 Valid cancellation
- TS-ORD-03 Invalid cancellation/state transition
