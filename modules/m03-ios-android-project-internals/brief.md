# M03 — iOS and Android Project Basics

**Week 1 · Day 3 · 5 hours**

## Builds on

[M02](../m02-community-modules-native-linking/write-up-template.md) — the profile app with its
first linked native modules is what gets three environments here.

## Objective

Get comfortable enough with the native project files to set app identity for three environments —
using EAS Build profiles instead of hand-editing Xcode schemes or Gradle flavors.

## Scope

- App identity basics: bundle ID / application ID, app name, version number vs. build number, app
  icon and splash screen — all set through `app.config.js`, not edited by hand in Xcode or Android
  Studio.
- EAS Build profiles (`eas.json`): how `development`, `preview` and `production` profiles map to
  Dev, Staging and Prod, each with its own app identity.
- A light read-through of the generated `ios/` and `android/` folders (via `npx expo prebuild`) so
  they're not a black box — you're finding where things end up, not editing them.
- Custom URL schemes.
- Android `minSdk`/`compileSdk`/`targetSdk`, at a glance, and why store rules push `targetSdk` up
  every year.

## Stack constraints

- Same pins as M01–M02. EAS account (free tier) from M02.

## Resolved: three environments via EAS build profiles

Every learner sets up Dev, Staging and Prod as EAS build profiles, each with its own app identity
configured through `app.config.js` — not hand-made Xcode schemes or Gradle product flavors. If you
want the deeper by-hand path later, the capstone's Workshop D is where that option lives.

## Deliverable

**Three EAS build profiles (Dev, Staging, Prod) for the profile app, each producing its own
installable build with a distinct name, icon and bundle ID, triggered with one `eas build` command
per profile.**

## Lab

*Goal: get a working multi-environment setup fast, without hand-editing native project files.*

**You do.**

1. Configure `app.config.js` to vary app name, icon, and bundle ID/application ID by environment.
2. Set up `development`, `preview` and `production` profiles in `eas.json`, mapped to Dev, Staging
   and Prod.
3. Run `eas build` for each profile and install all three on one device or simulator.
4. Confirm all three identities show up correctly and don't collide.
5. Run `npx expo prebuild` once and skim the generated `ios/`/`android/` folders just enough to find
   where the bundle ID and version number actually live.

**You build and capture.** Three installable builds from three EAS profiles, installed side by
side, plus a short note on what you found when you skimmed the native folders.

## Definition of done

- [ ] Three EAS build profiles exist and each builds successfully.
- [ ] All three installs sit on one device/simulator at once with distinct names and icons.
- [ ] You can point to where the bundle ID and version number end up in the native folders.
