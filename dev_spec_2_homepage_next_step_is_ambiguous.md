# Homepage next step is ambiguous — dev spec
Site: domesticdomestic.com · Priority 2 · Medium · Effort: Low (0.5-2 days)

## Problem
The homepage presents multiple unrelated CTAs and social follow headings, leaving no clear primary direction into the purchase path.

## Evidence (from the live site)
> 5 distinct calls to action compete on the same page: “Create account”, “Check out”, “Shop now”, “See More”, “shop@domesticdomestic.com”.
> The page's main headline reads “Follow us on Instagram”.
> The page's main headline reads “Follow us on Facebook”.

## Current state
h1: Follow us on Instagram; cta: Shop now; notes: Multiple CTAs, social headings

## Required change
h1: Shop new arrivals; cta: Shop now; notes: Single dominant browse CTA

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Single dominant browse CTA
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_homepage_next_step_is_ambiguous` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
