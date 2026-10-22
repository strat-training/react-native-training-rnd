# M08 Write-Up — Real-Time Sync and Offline

> Fill this in as you go. Write it so a trainee starting this stage next cohort could follow your
> path on their own.

## What I built

Live sync across two devices and offline-safe editing for the to-do list.

## Why it's built this way (key decisions)

- Where exactly do you set up and tear down your snapshot listeners, and why there?
- What happens in your app when two edits to the same to-do collide? Is last-write-wins actually
  good enough here, and how do you know?

## How to build it (teach it to the next trainee)

Write a guide to building a list screen that stays correct offline and resyncs cleanly, using the
airplane-mode test as the worked example.

## Concepts worth explaining

Pick 1-2 ideas — Firestore's offline persistence model, or the difference between a pending write
and a synced one — and explain each in your own words.

## What tripped me up

Listener cleanup bugs, conflicting-write surprises, anything the two-device test caught that a
single-device test wouldn't have.

## Checkpoint evidence

Show the airplane-mode test script passing, with both devices ending in the same state.

## What I'd do differently

If you started this module over, what would you do differently?
