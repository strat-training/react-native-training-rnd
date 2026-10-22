# M02 — Community Modules and Native Linking

**Week 1 · Day 2 · 4 hours**

## Builds on

[M01](../m01-toolchain-hybrid-project-setup/write-up-template.md) — the `PersonalProfileApp`
skeleton from a working toolchain is what this stage adds its first real dependencies to.

## Objective

For any given need, decide whether an Expo package, a community module or custom native code fits
best — and install and link a community module by hand.

## Scope

- The hybrid rule: community modules for core features, small Expo utilities only where they are
  easy to replace later.
- How native linking actually works: autolinking, `pod install`, Gradle changes, and how an icon
  font gets registered on each platform (`UIAppFonts` in `Info.plist`, a Gradle script on Android).
- `@react-native-async-storage/async-storage`, `react-native-safe-area-context` and
  `react-native-vector-icons` as the three modules to add this stage.
- How to judge whether a community module is safe to depend on: recent releases, New Architecture
  support, fit with React Native 0.88, a check on React Native Directory.
- What EAS Build and EAS Submit do: `eas build` builds both platforms from your committed native
  folders, `eas submit` uploads to App Store Connect/TestFlight and the Play Console — the course's
  build tool from here through the capstone.
- `expo prebuild` versus committed native folders, and why this course keeps and hand-manages the
  committed folders instead.

## Stack constraints

- Same pins as M01. Install SDK-aligned libraries with `npx expo install` so you never guess a
  version by hand.
- EAS account (free tier) needed for builds from here on.

## Deliverable

**The profile app with AsyncStorage, vector icons and safe-area-context linked and working on both
platforms, plus a one-page lock-in audit of every dependency added so far.**

## Lab

*Goal: get comfortable linking native code by hand, and build the habit of asking what happens if a
dependency disappears before you take it on.*

**You do.**

1. Add `@react-native-async-storage/async-storage`, `react-native-safe-area-context` and
   `react-native-vector-icons` to the profile app.
2. Link each one by hand where autolinking needs help — in particular, register the icon font on
   both platforms yourself rather than relying on a template that already did it.
3. For each dependency, check: last release date, New Architecture support, and its standing on
   React Native Directory.
4. Write a one-page lock-in audit: every dependency, who maintains it, what happens if it stops
   being maintained, and your exit plan if it does. Ask your trainer for the filled-in example row
   to match the format against.
5. Run `npx expo-doctor` again and resolve anything new it flags.

**You build and capture.** The three modules working on both platforms, and the lock-in audit ready
for review.

## Definition of done

- [ ] All three modules are linked and visibly working on both platforms.
- [ ] The lock-in audit covers every dependency added so far, matches the example row's format, and
      passes instructor review.
- [ ] `npx expo-doctor` reports no errors.
