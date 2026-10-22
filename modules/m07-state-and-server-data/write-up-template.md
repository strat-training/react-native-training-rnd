# M07 Write-Up — State and Server Data

> Fill this in as you go. Write it so a trainee starting this stage next cohort could follow your
> path on their own.

## What I built

The to-do store, the service layer, optimistic updates, and the Firebase-behind-services lint rule.

## Why it's built this way (key decisions)

- How did you implement the optimistic update and its rollback, specifically?
- What does your service layer's interface look like, and where exactly does Zod validation sit in
  it?
- How did you enforce that only the service layer touches Firebase — what's the actual lint rule?

## How to build it (teach it to the next trainee)

Write a guide to building an optimistic-update flow with a clean rollback path, using your own
to-do store as the worked example.

## Concepts worth explaining

Pick 1-2 ideas — the three-way state split (Zustand/Context/TanStack Query), or what actually makes
an optimistic update safe to roll back — and explain each in your own words.

## What tripped me up

Rollback edge cases, cache invalidation surprises, anything that made the lint rule harder than
expected.

## Checkpoint evidence

Show a forced save failure rolling back the optimistic update and surfacing an error.

## What I'd do differently

If you started this module over, what would you do differently?
