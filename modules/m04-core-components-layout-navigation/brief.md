# M04 — Core Components, Layout and Navigation

**Week 1 · Day 4-5 · 5 hours**

## Builds on

[M03](../m03-ios-android-project-internals/write-up-template.md) — the three variants from that
stage are what the Personal Profile App's real screens now get built on top of.

## Objective

Build production screens from core components, set up stack and tab navigation, and handle safe
areas, the keyboard, dark mode and basic accessibility.

## Scope

- `View`, `Text`, `Image`, `ScrollView`, `Pressable`, `TextInput` and `FlatList`.
- Flexbox layout, `StyleSheet`, and keeping a small set of consistent design tokens. NativeWind
  (Tailwind-style utility classes for React Native) is a documented optional alternative to
  `StyleSheet` — ask your trainer whether this cohort allows it. `StyleSheet` is the default, and
  the checkpoint doesn't care which one you used, only that the screens actually meet it.
- Safe areas and window changes (resizable iPhone windows on iOS 27, foldables).
- Keyboard handling.
- Dark mode and dynamic text size.
- React Navigation: stack and tab navigators, typed params, the native dependencies it needs
  (`react-native-screens`, `react-native-gesture-handler`).
- API changes worth knowing: the Strict TypeScript API is the default (typed refs, no deep
  imports), `InteractionManager` is removed, `ImageBackground` is deprecated.

## Stack constraints

- Same pins as M01–M03. React Navigation: current stable major — confirm which one with your
  trainer at the start of this module (it moves fast; don't assume it's still the version from when
  this brief was written).
- Optional: NativeWind, if your trainer confirms this cohort allows it in place of `StyleSheet`. It
  adds a Babel/Metro config step and a dependency you'd then track against every Expo SDK upgrade —
  weigh that against the typing-speed win before you install it.

## Deliverable

**The Personal Profile App: Profile, Edit Profile and Settings screens, with a working theme
toggle, validated edit form, persisted data, and an accessibility checklist the screens pass.**

## Lab

*Goal: go from core components to real, navigable, accessible screens — and build the accessibility
checklist you'll reuse for the rest of the course.*

**You do.**

1. Set up stack and/or tab navigation across Profile, Edit Profile and Settings.
2. Build the Profile screen and the Edit Profile screen, with form validation for name length,
   email format and phone format.
3. Build the Settings screen: a dark/light theme toggle, an app version line, and a "clear all
   data" button.
4. Persist the profile data in AsyncStorage so it survives an app restart.
5. Handle safe areas and the keyboard correctly on both platforms.
6. Write a short accessibility checklist (labels, roles, dynamic type, a screen reader pass at
   minimum) and run your screens against it. You'll reuse this same checklist in M09 and the
   capstone, so make it something you'd trust again.

**You build and capture.** The three screens working and navigable on both platforms, data
surviving a restart, and your accessibility checklist with its results.

## Definition of done

- [ ] Data survives an app restart.
- [ ] Navigation works correctly on both platforms.
- [ ] The accessibility checklist passes, and the checklist itself is written down for reuse.
