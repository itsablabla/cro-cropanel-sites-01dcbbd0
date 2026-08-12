# Sale promo competes with checkout — dev spec
Site: domesticdomestic.com · Priority 7 · Urgent · Effort: Medium (2-5 days)

## Problem
The sitewide sale banner on the cart page offers an exit from the purchase path at the final step before conversion.

## Evidence (from the live site)
> ADDITIONAL 20% OFF ON SALE ITEMS | SHOP SALE!
> 4 distinct calls to action compete on the same page: “Create account”, “Check out”, “See More”, “shop@domesticdomestic.com”.
> The page's main headline reads “Your cart”.

## Current state
h1: Your cart; cta: Check out; notes: Sale banner sits beside Check out

## Required change
h1: Your cart; cta: Check out; notes: Remove or de-emphasize sale banner

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Remove or de-emphasize sale banner
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_sale_promo_competes_with_checkout` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
