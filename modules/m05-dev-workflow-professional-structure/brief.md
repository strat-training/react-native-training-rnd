# M05 — Dev Workflow and Professional Structure

**Week 1 · Day 5 · 2 hours**

## Builds on

[M04](../m04-core-components-layout-navigation/write-up-template.md) — the working, navigable
profile app is what gets reorganized into a maintainable structure here.

## Objective

Choose the right debug and build loop for a given change, and organize the project so a team could
actually work in it.

## Scope

- Development builds versus Expo Go, and why this course uses development builds throughout (Expo
  Go cannot load most of the community native modules you've already linked).
- Fast Refresh, and recognizing when a change needs a native rebuild instead.
- Debugging with React Native DevTools (the current replacement for Flipper) and its network
  inspector.
- Project structure: `components`, `navigation`, `services`, `utils`, `assets`.
- A storage service that wraps AsyncStorage behind a clean interface.
- TypeScript, ESLint and Prettier.
- Migration strategies: what it would take to drop Expo tooling later, and what it would take to
  add more Expo packages later.

## Stack constraints

- Same pins as M01–M04.

## Deliverable

**The profile app moved into a standard folder layout, with a storage service wrapping
AsyncStorage, TypeScript and lint passing, and the app still running on both platforms.**

## Lab

*Goal: turn a working app into a structure a second engineer could join without a tour.*

**You do.**

1. Move the profile app into the standard folder layout (`components`, `navigation`, `services`,
   `utils`, `assets`).
2. Build a storage service that wraps AsyncStorage, and route all persistence through it instead of
   calling AsyncStorage directly from screens.
3. Set up TypeScript, ESLint and Prettier (or confirm and tighten whatever you already have from
   earlier modules).
4. Re-run the app on both platforms after the move and confirm nothing broke.
5. **Take-home bonus (not scheduled, not graded):** rebuild the same app with
   `react-native init`, copy your `src/` folder across unchanged, and compare the two setups. Worth
   doing if you want a clearer sense of exactly what Expo's tooling is doing for you.

**You build and capture.** TypeScript and lint both passing, and the app running on both platforms
after the restructure.

## Definition of done

- [ ] TypeScript and lint both pass.
- [ ] The app still runs on both platforms after the folder move.
- [ ] All persistence goes through the storage service, not directly through AsyncStorage.
