# M01 — Toolchain and Hybrid Project Setup

**Week 1 · Day 1 · 4 hours**

## Builds on

None — this is the first stage.

## Objective

Set up a clean machine for iOS and Android builds, create a bare React Native project on Expo's
tooling, and explain what happens between `npx expo start` and pixels on a screen.

## Scope

- Required tools: Xcode, Android Studio, JDK, Node.js, Watchman, Ruby/Bundler and CocoaPods.
- The bare-workflow idea itself: `ios/` and `android/` are yours, committed to Git. You build and
  run with Expo's tooling throughout — Expo Go, dev builds and EAS Build all stay in play.
- Two ways to start a bare project with Expo tooling, and when each one fits: `npx create-expo-app
  --template bare-minimum`, versus a managed Expo project plus `expo-dev-client`.
- Project layout: `ios/`, `android/`, `app.json`, `metro.config.js`, `babel.config.js`.
- How a build actually works: Metro bundles the JavaScript, Hermes runs it, the native app hosts it.
- Running the app with `npx expo start`, `npx expo run:ios` and `npx expo run:android`.
- Diagnosing setup problems with `npx expo-doctor`.
- Expo Go, for quick JS-only previews before Module 2 links your first community native module —
  and EAS Build, Expo's cloud build service, as your build tool for the rest of the course,
  including the capstone's release candidates.

## Stack constraints

- React Native 0.88, Expo SDK 58, React 19.3.0, Node.js 24 LTS, New Architecture always on.
- Xcode 26.4 or newer, Android `compileSdk` 37 / `targetSdk` 36.
- Free tools only, plus an EAS account (free tier covers this course).

## Resolved: native folders stay committed, EAS Build is the course's build tool

`ios/` and `android/` are committed to Git — that's the "bare workflow" part this program keeps.
Building and running day to day stays simple and Expo-first throughout: Expo Go for pure-JS screens
until Module 2 links your first native module, then dev builds, with EAS Build as the tool that
produces every build from here through the capstone's release candidates. A fully manual Xcode/
Gradle build is something you can choose instead later if you want the extra depth, but it's never
the required path.

## Deliverable

**A `PersonalProfileApp` skeleton that a fresh clone can build and run on both platforms using only
the README — with three planted setup faults found and fixed along the way.**

## Lab

*Goal: stand up the toolchain once, correctly, and prove it by debugging the setup problems a new
teammate would actually hit.*

**You do.**

1. Install and verify the full toolchain: Xcode, Android Studio, JDK, Node (pinned version),
   Watchman, Ruby/Bundler and CocoaPods.
2. Create `PersonalProfileApp` using the course's starter path, and confirm which Expo SDK version
   it actually installs.
3. Run the app on an iOS simulator and an Android emulator, then on one real device if you have
   one.
4. Write a README section that gets a stranger from clone to running app with no extra context.
5. Ask your trainer for the three planted setup faults (wrong Node version, a missing Pod install,
   a bad `ANDROID_HOME`) and fix each one, noting the symptom and the fix for your write-up.
6. Run `npx expo-doctor` and resolve everything it flags.

**You build and capture.** A fresh clone of your repo building and running on both platforms from
the README alone, and your own walkthrough of what happens between `npx expo start` and pixels on
screen.

## Definition of done

- [ ] A fresh clone builds and runs on both platforms using only the README.
- [ ] `npx expo-doctor` reports no errors.
- [ ] All three planted setup faults are fixed, with the symptom and fix written down.
- [ ] You can narrate, in your own words, the path from `npx expo start` to the app running on a
      device.

## Logistics

- Confirm with your trainer, before Day 1: the exact Xcode version for this cohort (the stack
  targets Xcode 26.4+, but confirm whether this cohort tests on a newer major), and whether
  `create-expo-app --template bare-minimum` actually installs SDK 58 at freeze time — if it
  doesn't, your trainer will tell you to use `init` plus `install-expo-modules` instead.
- Download the Xcode and Android Studio installers before Day 1 if you can — the 4 hours should go
  to learning, not waiting on large downloads.
