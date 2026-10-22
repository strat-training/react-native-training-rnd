# M10 Write-Up — Push Notifications with FCM

> Fill this in as you go. Write it so a trainee starting this stage next cohort could follow your
> path on their own.

## What I built

End-to-end push for a shared/assigned to-do, including the sending script and the tap-to-open
handling.

## Why it's built this way (key decisions)

- How does your local Node script decide when to send a push, and what does its payload look like?
- How did you handle the three app states (foreground/background/quit) differently, if at all?

## How to build it (teach it to the next trainee)

Write a guide to delivering a push notification end to end on both platforms, using your own
sending script and tap-handling code as the worked example.

## Concepts worth explaining

Pick 1-2 ideas — why Cloud Functions need a paid plan and what a local Admin SDK script replaces,
or why Android 13+ needs an explicit runtime permission for notifications — and explain each in
your own words.

## What tripped me up

APNs key setup, token registration surprises, permission-denied edge cases, anything that only
showed up on a real device.

## Checkpoint evidence

Show push working on a real iPhone and a real Android device, and the denied-permission path not
crashing.

## What I'd do differently

If you started this module over, what would you do differently?
