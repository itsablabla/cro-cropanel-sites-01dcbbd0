# Gift card prices ambiguous — dev spec
Site: domesticdomestic.com · Priority 8 · High · Effort: Medium (2-5 days)

## Problem
Gift card amounts render without decimal separators, leaving the actual price unclear and potentially misleading.

## Evidence (from the live site)
> Prices shown on the page: $881 $1762 $2202 $6607 $4405 $8809

## Current state
notes: Prices like $881

## Required change
notes: Format as $8.81, $17.62, etc.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Format as $8.81, $17.62, etc.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_gift_card_prices_ambiguous` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
