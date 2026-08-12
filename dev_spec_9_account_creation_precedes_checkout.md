# Account creation precedes checkout — dev spec
Site: domesticdomestic.com · Priority 9 · Medium · Effort: Medium (2-5 days)

## Problem
Create account is promoted ahead of Check out in the cart area, adding a non-purchase step to the primary conversion path.

## Evidence (from the live site)
> 4 distinct calls to action compete on the same page: “Create account”, “Check out”, “See More”, “shop@domesticdomestic.com”.
> Menu Search Log in Create account 0 Cart Item added to your cart View my cart (0) Check out Continue shopping

## Current state
cta: Create account | Check out; notes: Create account listed before Check out

## Required change
cta: Check out; notes: Check out first, guest checkout available

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Check out first, guest checkout available
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_account_creation_precedes_checkout` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
