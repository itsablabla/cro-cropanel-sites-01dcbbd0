# Order change page pushes checkout — dev spec
Site: domesticdomestic.com · Priority 10 · Medium · Effort: Medium (2-5 days)

## Problem
The page meant for changing an order offers checkout as the visible action, forcing users to find another route for their actual task.

## Evidence (from the live site)
> The page's main headline reads “Making Changes to Your Order”.
> 3 distinct calls to action compete on the same page: “Create account”, “Check out”, “shop@domesticdomestic.com”.

## Current state
h1: Making Changes to Your Order; cta: Check out; notes: No explicit manage action

## Required change
h1: Making Changes to Your Order; cta: Manage my order; notes: Add explicit manage action

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add explicit manage action
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_order_change_page_pushes_checkout` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
