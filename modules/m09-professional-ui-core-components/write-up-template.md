# M09 Write-Up — Professional UI and Core Components

> Fill this in as you go. Write it so a trainee starting this stage next cohort could follow your
> path on their own.

## What I built

The Paper-themed, swipe-enabled, performance-tuned to-do list, and its accessibility re-pass.

## Why it's built this way (key decisions)

- What did the profiler actually show you was re-rendering, and what did you change to fix it?
- What's different about your list in the release build versus debug, and why did that difference
  matter for the 2,000-item test?

## How to build it (teach it to the next trainee)

Write a guide to tuning a `FlatList` for a long, frequently-updated list, using your own before/after
profiler results as the worked example.

## Concepts worth explaining

Pick 1-2 ideas — why debug and release builds perform differently, or what actually makes a
`FlatList` row re-render — and explain each in your own words.

## What tripped me up

Performance surprises, gesture/animation conflicts, anything the accessibility re-pass caught that
the first pass in M04 missed.

## Checkpoint evidence

Show the 2,000-item scroll performance in a release build, and the accessibility checklist passing.

## What I'd do differently

If you started this module over, what would you do differently?
