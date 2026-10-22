# M03 Write-Up — iOS and Android Project Basics

> Fill this in as you go. Write it so a trainee starting this stage next cohort could follow your
> path on their own.

## What I built

Three EAS build profiles (Dev, Staging, Prod) for the profile app, each with its own identity.

## Why it's built this way (key decisions)

- How did you structure `app.config.js` to vary identity by environment, and what did you end up
  putting in `eas.json` versus `app.config.js`?
- What did you find when you skimmed the generated native folders — where do the bundle ID and
  version number actually live?

## How to build it (teach it to the next trainee)

Write a guide to standing up Dev/Staging/Prod as EAS build profiles that install side by side,
using your own `app.config.js`/`eas.json` as the worked example.

## Concepts worth explaining

Pick 1-2 ideas — what an EAS build profile actually controls, or why the native folders still need
to be committed even though EAS does the building — and explain each in your own words.

## What tripped me up

Identity collisions between profiles, anything confusing about where `app.config.js` vs. `eas.json`
settings apply.

## Checkpoint evidence

Show all three builds installed side by side on one device/simulator, with distinct names and
icons.

## What I'd do differently

If you started this module over, what would you do differently?
