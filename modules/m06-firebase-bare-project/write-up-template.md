# M06 Write-Up — Firebase on a Bare Project

> Fill this in as you go. Write it so a trainee starting this stage next cohort could follow your
> path on their own.

## What I built

The To-Do App's Firebase project, auth flow, Firestore data model and security rules.

## Why it's built this way (key decisions)

- What's your Firestore data model for to-dos, and why that shape?
- How did you write and prove your security rule — what did the failing case look like before you
  fixed it?

## How to build it (teach it to the next trainee)

Write a guide to wiring Firebase into a bare React Native project and locking data down per user,
using your own rules as the worked example.

## Concepts worth explaining

Pick 1-2 ideas — how Firestore security rules actually evaluate, or why config files need native
wiring instead of just an npm install — and explain each in your own words.

## What tripped me up

Config file placement, Gradle/Xcode wiring surprises, anything your first rules attempt got wrong.

## Checkpoint evidence

Show auth working on both platforms, and the proof that user B cannot read user A's data.

## What I'd do differently

If you started this module over, what would you do differently?
