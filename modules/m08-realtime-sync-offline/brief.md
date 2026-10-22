# M08 — Real-Time Sync and Offline

**Week 2 · Day 3 · 4 hours**

## Builds on

[M07](../m07-state-and-server-data/write-up-template.md) — the service-layer-backed to-do store is
what now needs to stay correct across two devices and no network.

## Objective

Keep two devices in sync in real time, and make the app genuinely useful with no network at all.

## Scope

- Firestore snapshot listeners, and cleaning them up correctly.
- Firestore offline persistence and pending writes.
- Network status with `@react-native-community/netinfo`.
- Simple conflict rules, and recognizing when last-write-wins genuinely isn't good enough.
- Testing sync across two devices (two simulators or emulators can stand in for real hardware).

## Stack constraints

- Same pins as M01–M07. NetInfo, pinned in your lockfile.

## Deliverable

**The to-do list updating live across two devices, surviving an airplane-mode edit, and syncing
back to a consistent state once the network returns.**

## Lab

*Goal: prove the app works with no network, not just that it works most of the time.*

**You do.**

1. Wire Firestore snapshot listeners into the to-do list so changes on one device show up live on
   another.
2. Turn on Firestore offline persistence and confirm pending writes behave the way you expect.
3. Add NetInfo so the app knows and can show its own connection state.
4. Write (or get from your trainer) an airplane-mode test script: edit on one device offline, bring
   it back online, confirm both devices end with the same data.
5. Run the test across two devices (or two simulators/emulators) and fix whatever the first run
   exposes.

**You build and capture.** The airplane-mode test script passing, with both devices ending in the
same state.

## Definition of done

- [ ] The airplane-mode test script passes.
- [ ] Both devices end with the same data after the network returns.
