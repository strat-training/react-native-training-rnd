# M09 — Professional UI and Core Components

**Week 2 · Day 4 · 4 hours**

## Builds on

[M08](../m08-realtime-sync-offline/write-up-template.md) — the sync-and-offline-safe to-do app now
gets the polish pass, and reuses the accessibility checklist you wrote in
[M04](../m04-core-components-layout-navigation/write-up-template.md).

## Objective

Build a polished, accessible and fast UI with a component library, and find simple performance
problems before they become real ones.

## Scope

- React Native Paper: theming, dark mode, common components.
- `FlatList` tuning: stable keys, memoized rows, avoiding unnecessary re-renders.
- Swipe gestures with Gesture Handler, and light animation with Reanimated.
- Loading, empty and error states.
- Forms and keyboard handling.
- Accessibility: labels, roles, dynamic type, a screen reader pass — reuse the checklist from M04.
- Finding re-renders with the React DevTools profiler.

## Stack constraints

- Same pins as M01–M08. React Native Paper, Gesture Handler, Reanimated, pinned in your lockfile.
- Measure scroll performance in a release build, not a debug build — debug builds are not
  representative.

## Deliverable

**The to-do app polished with a Paper theme, swipe-to-delete, loading/error states, and a release
build that scrolls 2,000 to-dos smoothly while passing the M04 accessibility checklist.**

## Lab

*Goal: make the app feel finished, and prove performance with numbers from a release build, not a
guess from a debug build.*

**You do.**

1. Apply a React Native Paper theme, including dark mode.
2. Add swipe-to-delete with Gesture Handler.
3. Build loading, empty and error states for the to-do list.
4. Tune the `FlatList` rendering 2,000 to-dos: stable keys, memoized rows, and whatever else the
   profiler tells you is re-rendering unnecessarily.
5. Build a release build and confirm the scroll is smooth with 2,000 to-dos in it — not in debug.
6. Re-run the M04 accessibility checklist against the updated screens, including a screen reader
   pass on both platforms.

**You build and capture.** The release build's scroll performance with 2,000 to-dos, and the
accessibility checklist passing again on the updated screens.

## Definition of done

- [ ] 2,000 to-dos scroll smoothly in a release build.
- [ ] The accessibility checklist passes.
