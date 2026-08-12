# Conflicting cart feedback after add — dev spec
Site: domesticdomestic.com · Priority 6 · Urgent · Effort: Medium (2-5 days)

## Problem
The cart drawer simultaneously shows 'Item added' and 'View my cart (0)', confusing shoppers about whether their item was added.

## Evidence (from the live site)
> Item added to your cart View my cart (0) Check out Continue shopping

## Current state
cta: Check out; notes: Shows 'Item added' and 'View my cart (0)'

## Required change
cta: Check out; notes: Update cart count in success message

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Update cart count in success message
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_conflicting_cart_feedback_after_add` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
