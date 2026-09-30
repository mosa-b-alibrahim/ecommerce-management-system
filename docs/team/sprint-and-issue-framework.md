# Sprint & Issue Framework

## Sprint model
Start with one-week Sprints. Each Sprint has one outcome-focused Sprint Goal, a small set of Issues that support that goal, and a review at the end.

Do not pre-create detailed Issues for the entire project. Keep the full roadmap at phase/milestone level. Create detailed Issues for the current Sprint and, when useful, the next Sprint.

## Work hierarchy
Project -> Phase/Milestone -> Sprint -> Feature -> Issue -> Branch -> Pull Request -> Review/CI -> Merge.

## Board flow
Backlog -> Ready -> In Progress -> Code Review -> Testing -> Done.

## Issue sizing
- Small: about 2-4 focused implementation hours.
- Medium: about half a day to one day.
- Large: about 1-2 days and should usually be split further.
Learning time may make elapsed time longer; sizing refers to focused implementation scope.

## How to split a feature
Avoid: `Build Product Management`.
Prefer focused Issues such as:
1. Create Product entity/model.
2. Add Product database migration.
3. Add Product repository.
4. Add Product request/response DTOs.
5. Implement Product validation.
6. Implement create-product service behavior.
7. Add POST /api/v1/products.
8. Add create-product unit tests.
9. Add create-product integration/API tests.
10. Add get-product behavior.
11. Add list-products behavior.
12. Add pagination/sorting/filtering as separate Issues when appropriate.

## Required Issue content
Every implementation Issue should include:
- Goal / user or system value
- Dependencies
- Requirements / business rules
- Acceptance Criteria
- Required Tests
- Definition of Done
- Estimate/size
- Assignee
- Sprint/Milestone

## Definition of Done
An Issue is Done when:
- Acceptance Criteria are satisfied.
- Required tests are implemented and passing.
- No unrelated changes are included.
- Relevant documentation is updated.
- A focused Pull Request exists.
- The partner has reviewed it.
- Required CI checks pass.
- The branch is merged to main.

## Team ownership
Both contributors are developers and testers. Each contributor owns complete vertical slices: implementation plus tests. Rotate feature ownership. The contributor who did not implement the change should normally review the PR.

## Branch naming examples
- feature/27-create-product
- fix/44-checkout-stock-race
- test/58-order-api-regression
- docs/12-update-api-contract

## Sprint close
At Sprint end review:
- Sprint Goal achieved or not
- completed vs carried Issues
- defects and test results
- technical/documentation debt
- workflow problems
- next Sprint scope

Carry unfinished work intentionally; do not mark incomplete work Done merely to close a Sprint.
