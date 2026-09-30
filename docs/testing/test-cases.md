# Test Cases

## TC-CHK-001 Successful checkout
Preconditions: authenticated customer; active product; stock=5; cart quantity=2.
Action: checkout.
Expected: order created; two units deducted; order total equals server-calculated price; cart behavior matches documented policy.

## TC-CHK-002 Insufficient stock
Preconditions: stock=2; cart quantity=3.
Action: checkout.
Expected: rejected; no successful order; stock remains 2.

## TC-CHK-003 Concurrent final unit
Preconditions: stock=1; two authenticated customers each prepared to buy quantity=1.
Action: execute checkout requests concurrently.
Expected: at most one successful purchase; final stock never negative; no two successful orders consuming the same final unit.

## TC-SEC-001 Customer calls Admin product creation
Expected: forbidden; no product created.

## TC-ORD-001 Historical price
Precondition: order purchased product at 10.00.
Action: Admin changes current product price to 15.00.
Expected: historical order still shows purchase-time price 10.00.

More cases are added feature-by-feature from Issue acceptance criteria.
