# Ambiguous Accoutrement nav label — dev spec
Site: domesticdomestic.com · Priority 4 · Medium · Effort: Low (0.5-2 days)

## Problem
The brand tagline 'Culturally Charged Accoutrement' runs into the category list, and a separate 'Accoutrement' category appears, confusing shoppers.

## Evidence (from the live site)
> Culturally Charged Accoutrement Bags Travel Kits Key Chains Wallets Sunglasses Watches
> Jewelry Accoutrement Office Books

## Current state
notes: Tagline and category overlap

## Required change
notes: Rename category to 'Accessories'

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Rename category to 'Accessories'
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_ambiguous_accoutrement_nav_label` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
