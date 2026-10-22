# React Native Bare Workflow Training Curriculum (4-Week Version)

**The Expo Hybrid Approach for senior engineers**

Draft: October 21, 2026 · Revised: October 22, 2026 · Length: 4 weeks, about 80 hours · Format: Weeks 1–2 individual work, Weeks 3–4 team capstone

Based on the 10-week program in the `strat-training/bare-workflow-blueprint` repo, cut down to fit 4 weeks.

**October 22 revision:** aligned the build and release path with the source repo's own approach
(EAS Build, EAS Submit, Expo Go kept throughout) after reviewing its actual docs — the earlier draft
had assumed a fully by-hand, EAS-free build model that the source itself doesn't use. See Section 12.

---

## 1. Course Summary

This course teaches senior engineers how to build and ship production React Native apps on their own terms. You work in the **bare workflow**: the `ios/` and `android/` folders are yours, committed to Git from Day One.

You still get the best parts of Expo. This is the **Expo Hybrid Approach**: use Expo's tooling (Expo Go, dev builds, EAS Build) for a fast developer experience and a simple release process, and use community modules for your core features instead of locking into Expo's managed SDK. EAS Build and EAS Submit are the course's build and release tool throughout, including the capstone's signed release candidates — a fully by-hand Xcode/Gradle release is available as an optional deeper path, not a requirement.

The course follows the repo's path:

- **Week 1:** native setup and core components, building a Personal Profile App.
- **Week 2:** full-stack features, building a To-Do App with Firebase, state, offline sync and push.
- **Weeks 3–4:** a team capstone, AirlineBooker Pro, ending in signed release candidates for iOS and Android.

## 2. Who It Is For

Senior engineers who already build software professionally and want full control over mobile builds and deployments for iOS and Android.

**You should already:**

- Be comfortable with JavaScript or TypeScript and modern React (hooks, components, state)
- Use Git, a terminal and pull requests every day
- Understand REST APIs and token-based auth
- A Mac helps but isn't required for iOS work — EAS Build builds iOS in the cloud, so Windows and Linux learners can ship signed iOS release candidates too (a Mac is still useful for the iOS simulator and local debugging)

No mobile experience is needed. Basic Swift or Kotlin reading skills help but are not required.

## 3. What You Will Be Able To Do

By the end of the course, you can:

1. Set up the iOS and Android toolchains and create a bare React Native project with Expo tooling.
2. Read the native iOS and Android projects enough to set app identity, and manage Dev/Staging/Prod environments through EAS build profiles.
3. Choose between an Expo package, a community module and custom native code, and explain the choice.
4. Install and link community native modules by hand.
5. Build accessible screens with core components, React Navigation and a UI library.
6. Build full-stack features: Firebase auth and data, state management, real-time sync, offline use and push notifications.
7. Test and profile an app with unit tests, component tests, end-to-end flows and native profilers.
8. Make signed release builds and deliver them to TestFlight and the Google Play internal track with EAS Build and EAS Submit (and know the by-hand Xcode/Gradle path as an alternative).
9. Plan the architecture of a mobile app and work with a team through a release.

## 4. How the Course Works

**Two individual projects, then one team project.**

| Project | Week | Who | What |
| --- | --- | --- | --- |
| Personal Profile App | 1 | Individual | Profile, edit and settings screens with community modules |
| Full-Stack To-Do App | 2 | Individual | Firebase auth, real-time sync, offline, push |
| AirlineBooker Pro | 3–4 | Teams of 4–5 | Flight search and booking app, shipped to the store tracks |

**Module pattern.** Every module has learning objectives, topics, a hands-on lab and a checkpoint. A module is about 25% talk, 60% lab and 15% checkpoint. Each module names the repo folder it comes from.

**Backend.** Firebase (Auth, Firestore, Cloud Messaging) on its free tier. Supabase is shown as an alternative, but not built.

**Capstone scope.** Teams work through a priority list: must-haves first, then should-haves, then could-haves. This keeps a 2-week capstone realistic.

## 5. Course at a Glance

| Week | Phase | Module | Hours |
| --- | --- | --- | --- |
| 1 | Native setup | 1. Toolchain and Hybrid Project Setup | 4 |
| 1 | Native setup | 2. Community Modules and Native Linking | 4 |
| 1 | Native setup | 3. iOS and Android Project Basics | 5 |
| 1 | Core components | 4. Core Components, Layout and Navigation | 5 |
| 1 | Core components | 5. Dev Workflow and Professional Structure | 2 |
| 2 | Full-stack features | 6. Firebase on a Bare Project | 4 |
| 2 | Full-stack features | 7. State and Server Data | 4 |
| 2 | Full-stack features | 8. Real-Time Sync and Offline | 4 |
| 2 | Full-stack features | 9. Professional UI and Core Components | 4 |
| 2 | Full-stack features | 10. Push Notifications with FCM | 4 |
| 3–4 | Capstone (team) | 11. AirlineBooker Pro, with four workshops | 40 |
| | | **Total** | **80** |

## 6. How 10 Weeks Became 4

| Repo weeks | Repo content | In this 4-week version |
| --- | --- | --- |
| 1 | Hybrid setup, Personal Profile App | **Week 1.** Kept in full. Added lightweight native project basics via EAS build profiles (Module 3) |
| 2 | Full-stack To-Do App: Firebase, Zustand, offline, Paper UI | **Week 2.** Kept in full. Added push notifications (Module 10), moved up from repo Weeks 7–8 |
| 3–4 | Airline booking capstone: architecture, auth, navigation, search, booking, payment, tests | **Weeks 3–4.** Kept as the capstone. Payment becomes a should-have |
| 5–6 | Booking engine, seat selection, offline, biometrics, voice search, accessibility, performance | Offline is a must-have. Seat selection, accessibility and performance are should-haves. Biometrics and price alerts are could-haves. Voice search, multi-city trips, travel insurance and real-time prices are cut |
| 7–8 | Maps, push, real-time updates, chat, Live Activities, geofencing | Push is a must-have. Maps are a should-have. Chat, Live Activities, geofencing, flight tracking and background location are cut |
| 9–10 | Testing, store deployment, analytics, A/B tests | Testing and manual store deployment are must-haves (workshops). Crash reporting is a should-have. Analytics, store listing work and A/B tests are discussion only |

---

## 7. Module Details

## Week 1: Native Setup and Core Components (Personal Profile App)

### Module 1: Toolchain and Hybrid Project Setup (4 hours)

*From the repo: `week-01-hybrid`, Day 1.*

**Learning objectives**

- Set up a clean machine for iOS and Android builds.
- Create a bare React Native project that uses Expo's tooling.
- Run the app on a simulator, an emulator and a real device.
- Explain what happens between `npx expo start` and pixels on screen.

**Topics**

- Required tools: Xcode, Android Studio, JDK, Node.js, Watchman, Ruby/Bundler and CocoaPods
- The repo's two setup paths: Option A, `npx create-expo-app --template bare-minimum` (the course default), and Option B, a managed Expo project plus `expo-dev-client`. When each one fits
- Project layout: `ios/`, `android/`, `app.json`, `metro.config.js`, `babel.config.js`
- How a build works: Metro bundles JavaScript, Hermes runs it, the native app hosts it
- Running with `npx expo start`, `npx expo run:ios` and `npx expo run:android`
- Finding setup problems with `npx expo-doctor`
- Expo Go for quick JS-only previews, and EAS Build as the course's build tool from here through the capstone

**Hands-on lab**

Create `PersonalProfileApp` and run it on iOS and Android. Then fix three planted setup errors: the wrong Node version, a missing Pod install and a bad `ANDROID_HOME`.

**Checkpoint**

A fresh clone builds and runs on both platforms using only the steps in the README.

---

### Module 2: Community Modules and Native Linking (4 hours)

*From the repo: `week-01-hybrid`, Day 2, and `docs/expo-hybrid-approach.md`.*

**Learning objectives**

- Decide for each need whether to use an Expo package, a community module or custom native code.
- Install and link native modules by hand.
- Keep a clean exit from every hosted Expo service.

**Topics**

- The hybrid rule: community modules for core features, and small Expo utilities (for example `expo-constants` or `expo-device`) only where they are easy to replace
- The module choices table in Section 11
- How native linking works: autolinking, `pod install`, Gradle changes, fonts for icon libraries (`UIAppFonts` in `Info.plist`, Gradle script on Android)
- `@react-native-async-storage/async-storage`, `react-native-safe-area-context` and `react-native-vector-icons`
- How to judge a community module: recent releases, New Architecture support, fit with React Native 0.88, a check on React Native Directory
- What `eas build` and `eas submit` do: building both platforms from your committed native folders, then uploading to App Store Connect/TestFlight and the Play Console
- `expo prebuild` versus committed native folders. The course commits and hand-manages them

**Hands-on lab**

Add AsyncStorage, vector icons and safe-area-context to the profile app. Write a one-page **lock-in audit**: every dependency, who maintains it, what happens if it stops, and the exit plan.

**Checkpoint**

The lock-in audit passes instructor review, and `npx expo-doctor` reports no errors.

---

### Module 3: iOS and Android Project Basics (5 hours)

*Lighter than the 10-week repo's own native-internals material. Teaches app identity through EAS
build profiles instead of hand-edited Xcode schemes and Gradle flavors — the repo itself never asks
learners to hand-edit the native projects this deeply, so this module was trimmed to match.*

**Learning objectives**

- Get comfortable enough with the native projects to set app identity, without hand-editing them.
- Set up three environments as EAS build profiles.

**Topics**

- App identity basics: bundle ID / application ID, app name, version number versus build number, app icon and splash screen — set through `app.config.js`
- EAS build profiles (`eas.json`): `development`, `preview` and `production`, each carrying its own app identity
- A light read-through of the generated `ios/` and `android/` folders, so they're not a black box
- Custom URL schemes
- Android `minSdk`, `compileSdk` and `targetSdk`, at a glance, and why store rules force `targetSdk` up each year

**Hands-on lab**

Configure `app.config.js` and `eas.json` for **Dev, Staging and Prod** build profiles of the profile app. Run `eas build` for each and install all three side by side. Skim the generated native folders to find where the bundle ID and version number actually live.

**Checkpoint**

Three EAS build profiles each build successfully, all three install side by side on one device, and the learner can point to where the bundle ID and version number end up in the native folders.

---

### Module 4: Core Components, Layout and Navigation (5 hours)

*From the repo: `week-01-hybrid`, Day 3, and exercises 2 and 5.*

**Learning objectives**

- Build production screens from core components.
- Set up stack and tab navigation.
- Handle safe areas, the keyboard, dark mode and basic accessibility.

**Topics**

- `View`, `Text`, `Image`, `ScrollView`, `Pressable`, `TextInput` and `FlatList`
- Flexbox layout, `StyleSheet` and simple design tokens
- Safe areas and window changes (resizable iPhone windows on iOS 27, foldables)
- Keyboard handling
- Dark mode and dynamic text size
- React Navigation: stack and tab navigators, typed params, native dependencies (`react-native-screens`, `react-native-gesture-handler`)
- API changes to know: the Strict TypeScript API is the default (typed refs, no deep imports), `InteractionManager` is removed, `ImageBackground` is deprecated

**Hands-on lab**

Build the Personal Profile App: Profile, Edit Profile and Settings screens. Settings has a dark and light theme toggle, an app version line and a "clear all data" button. Add form validation for name length, email format and phone format. Save the data in AsyncStorage.

**Checkpoint**

Data is still there after an app restart, navigation works on both platforms, and the screens pass a short accessibility checklist.

---

### Module 5: Dev Workflow and Professional Structure (2 hours)

*From the repo: `week-01-hybrid`, Days 4–5, and the migration strategies.*

**Learning objectives**

- Choose the right debug and build loop for each kind of change.
- Organize a project so a team can work in it.

**Topics**

- Development builds versus Expo Go. Expo Go cannot load most community native modules, so the course uses development builds
- Fast Refresh, and when a native rebuild is needed
- Debugging with React Native DevTools (it replaces Flipper) and the network inspector
- Project structure: `components`, `navigation`, `services`, `utils`, `assets`
- A storage service that wraps AsyncStorage
- TypeScript, ESLint and Prettier
- Migration strategies: how to drop Expo tooling later, and how to add more Expo packages later

**Hands-on lab**

Move the profile app into the standard folder layout with a storage service. Take-home bonus from the repo: build the same app with `react-native init`, copy the `src/` folder across and compare the two setups.

**Checkpoint**

TypeScript and lint pass, and the app still runs on both platforms after the move.

---

## Week 2: Full-Stack Features (Full-Stack To-Do App)

### Module 6: Firebase on a Bare Project (4 hours)

*From the repo: `week-02-hybrid`, exercise 1 and the setup guide, and `docs/backend-integration-guide.md`.*

**Learning objectives**

- Connect a bare React Native app to Firebase.
- Sign users in and out.
- Protect data with security rules.

**Topics**

- React Native Firebase modules: `app`, `auth`, `firestore`, `messaging`
- Config files: `GoogleService-Info.plist` in `ios/`, `google-services.json` in `android/app/`, plus the Gradle and Xcode changes
- One Firebase app per environment (Dev, Staging, Prod) and how it ties to the build variants from Module 3
- Firebase Auth with email and password
- Firestore data model for to-dos
- Security rules. The repo's example lets any signed-in user read and write everything. We tighten it so each user can only touch their own documents
- Free tier limits. Supabase as an alternative backend (concept only)

**Hands-on lab**

Create the Firebase project and install the modules. Build sign-up, sign-in and sign-out screens. Write rules so each user can read and write only their own to-dos.

**Checkpoint**

Auth works on both platforms, and a rules test proves that user B cannot read user A's data.

---

### Module 7: State and Server Data (4 hours)

*From the repo: `week-02-hybrid`, exercise 2, and the capstone stack (Zustand, Context, React Query).*

**Learning objectives**

- Pick the right place for each kind of state.
- Make the UI feel instant while data saves in the background.

**Topics**

- Zustand stores: CRUD, selectors, persistence
- React Context for app-wide settings such as theme and auth session
- TanStack Query (React Query) for server state: caching, retries, mutations, invalidation
- Optimistic updates and rollback
- Error boundaries
- A service layer between screens and Firebase, with typed data (Zod at the edges)

**Hands-on lab**

Build the to-do store with create, read, update and delete. Add optimistic updates. Connect it to Firestore through a service layer.

**Checkpoint**

A forced save failure rolls the optimistic update back and shows an error message.

---

### Module 8: Real-Time Sync and Offline (4 hours)

*From the repo: `week-02-hybrid`, exercise 3.*

**Learning objectives**

- Keep two devices in sync in real time.
- Make the app useful with no network.

**Topics**

- Firestore snapshot listeners and cleaning them up
- Firestore offline persistence and pending writes
- Network status with `@react-native-community/netinfo`
- Simple conflict rules, and when last-write-wins is not enough
- Testing sync across two devices

**Hands-on lab**

Make the to-do list update live on two devices. Edit on one device in airplane mode, then bring it back online and watch it sync.

**Checkpoint**

An airplane-mode test script passes, and both devices end with the same data.

---

### Module 9: Professional UI and Core Components (4 hours)

*From the repo: `week-02-hybrid`, exercise 4.*

**Learning objectives**

- Build a polished, accessible and fast UI with a component library.
- Find simple performance problems.

**Topics**

- React Native Paper: theming, dark mode, common components
- `FlatList` tuning: stable keys, memoized rows, avoiding re-renders
- Swipe gestures with Gesture Handler, and light animation with Reanimated
- Loading, empty and error states
- Forms and keyboard handling
- Accessibility: labels, roles, dynamic type, a screen reader pass
- Finding re-renders with the React DevTools profiler

**Hands-on lab**

Polish the to-do app: a Paper theme, swipe-to-delete, loading and error states. Do a screen reader pass on both platforms.

**Checkpoint**

A list of 2,000 to-dos scrolls smoothly in a release build, and the accessibility checklist passes.

---

### Module 10: Push Notifications with FCM (4 hours)

*From the repo: the messaging package in the Week 2 setup guide, repo Weeks 7–8 (push), and the FCM notes in `docs/backend-integration-guide.md`.*

**Learning objectives**

- Deliver push notifications through Firebase Cloud Messaging without any hosted push service from Expo.

**Topics**

- `@react-native-firebase/messaging`
- Permissions: the iOS prompt and the Android 13+ notification permission
- APNs key setup in Firebase, device tokens, Android notification channels
- Foreground, background and quit states
- Opening a screen when the user taps a notification
- Sending a push from a local Node script with the Firebase Admin SDK. This avoids Cloud Functions, which need a paid Firebase plan
- Why we skip the Expo push service: it adds a hosted dependency

**Hands-on lab**

Send a push when a to-do is shared or assigned, and open that item when the user taps it. Test foreground, background and quit states.

**Checkpoint**

It works on a real iPhone and a real Android device, and the denied-permission path does not crash.

---

## Weeks 3–4: Collaborative Capstone

### Module 11: AirlineBooker Pro (40 hours, with four workshops)

*From the repo: `week-03-04`, with parts of `week-05-06`, `week-07-08`, `week-09-10`, `capstone-projects` and `docs/deployment-guide.md`.*

**Learning objectives**

- Work as a team on one codebase with pull requests and code review.
- Design a clean app structure and keep to it under time pressure.
- Plan, build and ship a release candidate of a real-world app.

**The brief (default)**

**AirlineBooker Pro:** users sign in, search flights, pick one, enter passenger details, book it and see their bookings. You can swap in any of the repo's alternative briefs (event ticketing, marketplace, seat booking and others in `capstone-projects`). The same scope tiers apply.

**Data.** Flights come from a seeded Firestore collection, not the Aviation Stack API, so free-tier limits do not slow the team down. Real data is optional.

**Team setup.** Teams of 4–5. Roles rotate every two days: tech lead, release owner, UI owner, data and sync owner, quality owner. Every change goes through a pull request with one reviewer.

**Scope tiers**

| Tier | Features |
| --- | --- |
| **Must have** | Firebase sign-up and sign-in with an auth-guarded navigation flow. Flight search with filters (from, to, date, passengers) and a results list. Flight detail, passenger form and booking saved to Firestore. "My Bookings" that also opens offline. Push notification for a booking confirmation that opens the booking. Dev, Staging and Prod variants. Unit and component tests, and one end-to-end flow. Signed iOS and Android release candidates in TestFlight and the Play internal track |
| **Should have** | Seat selection. Payment with Stripe in test mode. A map of the airport or destination. Crash reporting. Accessibility and performance pass |
| **Could have** | Biometric unlock. Haptic feedback. Price alerts. Boarding-pass scan with the camera |
| **Cut from the 10-week plan** | Voice search, multi-city trips, travel insurance, real-time prices, chat support, Live Activities, geofencing, flight tracking, background location, A/B tests |

**Stack (from the repo, with changes listed in Section 12)**

TypeScript, React Navigation, Zustand and Context, TanStack Query, Firebase (Auth, Firestore, Messaging), `react-native-keychain`, `react-native-maps`, `@stripe/stripe-react-native`, Jest and React Native Testing Library, and an end-to-end tool (see Section 13).

**Project structure (from the repo)**

`src/` with `components`, `screens`, `navigation`, `services`, `store`, `context`, `hooks`, `utils`, `types` and `constants`, plus `__tests__/`, `docs/` and `guides/`.

**Plan**

| Week | Day | Hours | Focus | Exit goal |
| --- | --- | --- | --- | --- |
| 3 | 1 | 4 | Kickoff and **Workshop A: Architecture** | Architecture decisions written down. Repo, CI (lint, type-check, tests), variants, Firebase projects and seed data ready. Work split into vertical slices |
| 3 | 2 | 4 | Auth and navigation | Sign-up, sign-in, secure session, auth-guarded navigation |
| 3 | 3 | 4 | Flight search | Search form, filters and a fast results list |
| 3 | 4 | 4 | Flight detail and booking | Passenger form, booking saved, My Bookings screen |
| 3 | 5 | 4 | Integration, mid-point demo and **Workshop B: Testing** | Demo to instructors, first round of code review, tests in CI |
| 4 | 6 | 4 | **Workshop D, part 1: Release with EAS** (2 hours), then payments or seat selection | First signed skeleton build in TestFlight and Play internal track |
| 4 | 7 | 4 | Offline and push | My Bookings works offline, booking confirmation push opens the booking |
| 4 | 8 | 4 | Maps, could-haves and **Workshop C: Performance and crash reporting** | Release-mode profile, crash reports with readable traces |
| 4 | 9 | 4 | End-to-end tests and hardening | Tests green, accessibility pass, release branch cut |
| 4 | 10 | 4 | **Workshop D, part 2: Release candidate**, demo and retro | Signed builds installed by testers from both store tracks |

**Workshop A: Architecture (2 hours, Day 1)**

- Clean architecture and separation of concerns
- Folder layout, naming and import rules
- Custom hooks, Zustand with Context, error boundaries
- Writing short architecture decision records

**Workshop B: Testing (2 hours, Day 5)**

- Jest and React Native Testing Library, mocking native modules and Firebase
- What to test: auth, booking flow, offline cases, error cases
- One end-to-end flow (login, search, book) with Detox or Maestro
- CI on GitHub Actions for lint, type-check and unit tests

**Workshop C: Performance and Crash Reporting (2 hours, Day 8)**

- Profiling with React Native DevTools, Xcode Instruments and Android Studio Profiler
- List tuning, image loading, startup time, bundle size
- Crash and error reporting with Sentry or Firebase Crashlytics, including dSYM and R8 mapping uploads

**Workshop D: Build and Deploy with EAS (6 hours, split across Days 6, 9 and 10)**

*From the repo: `docs/deployment-guide.md`, using `eas build` and `eas submit` — the repo's own "recommended" path — with the local Xcode/Android Studio path offered as an alternative for teams that want it.*

- `eas.json` build profiles; Apple Developer team roles and credentials (EAS-managed or your own)
- `eas build --profile production` for both platforms
- `eas submit` to App Store Connect/TestFlight and the Play internal track
- Store build rules: see the version table in Section 11
- Version and build number scheme, release notes and staged rollouts
- Release checklist, hotfix and rollback process
- By-hand alternative, for teams that want it: certificates, provisioning profiles, archiving with Xcode or `xcodebuild`, Android keystores, `./gradlew bundleRelease`
- Discussion only: over-the-air updates (see Section 12), store listing basics, analytics and post-launch monitoring

**Checkpoint**

Teams demo a working app, and a tester installs both signed builds from the store tracks. If your cohort has no store accounts, see the open decisions in Section 13.

---

## 8. Assessment

| Part | Weight | How it is judged |
| --- | --- | --- |
| Module checkpoints | 25% | Pass or fail per module, reviewed by the instructor |
| Individual projects | 25% | Personal Profile App (end of Week 1) and Full-Stack To-Do App (end of Week 2) |
| Capstone | 50% | Team rubric below, plus individual contribution from pull requests |

**Capstone rubric (100 points)**

| Area | Points |
| --- | --- |
| Architecture and code quality | 20 |
| Features working, including offline and push | 20 |
| Native build and release ownership | 20 |
| Tests and quality tooling | 15 |
| Teamwork and code review | 15 |
| Demo and retro | 10 |

**To pass:** 70% overall, all must-have features working, and signed release candidates for both platforms.

## 9. Final Outcome

A graduate can take an idea and a design, choose a sensible stack, set up the native projects, build the features, test them and put signed builds in front of real testers, without depending on any hosted build service.

---

## 10. Tools and Costs

**Free tools:** VS Code, Android Studio, Xcode, EAS Build (free tier), Firebase free tier, Jest, React Native Testing Library, GitHub Actions (public repos), Stripe test mode.

**Costs you cannot avoid for the deploy workshop:** an Apple Developer Program membership ($99 a year, per the repo's deployment guide) and a Google Play Console account ($25 one time, same guide). Check current prices.

## 11. Versions and Module Choices

Versions below were checked on October 21, 2026. Pin exact versions per cohort and check again before each run.

| Item | Course choice | Status and notes |
| --- | --- | --- |
| React Native | 0.88 | Stable, released mid-October 2026. No user-facing breaking changes. Adds opt-in Swift Package Manager tooling |
| Expo SDK | 58 | Stable since October 15, 2026. Targets React Native 0.88. Built for iOS 27 |
| React | 19.3.0 | Matches Expo SDK 58 in the Expo docs table |
| Node.js | 24 LTS | Expo SDK 58 accepts 22.13+, 24.3+ and 26+. Odd-numbered releases are not supported |
| New Architecture | Always on | Legacy architecture support ended after Expo SDK 54. Every community module must support it |
| TypeScript | Strict TypeScript API | Default since React Native 0.87. Deep imports from `react-native/Libraries/*` are type errors |
| React Navigation | Current stable major | The repo says version 6. Version 8 is still in alpha, so check which stable major is current when you pin |
| Xcode | 26.4 or newer | Expo SDK 58 docs list 26.4+. Apple has required Xcode 26 builds for App Store uploads since April 28, 2026. Xcode 27 is open, see Section 13 |
| Android | compileSdk 37, targetSdk 36 | Expo SDK 58 values. Google Play requires new apps and updates to target API 36 since August 31, 2026 |
| Android release builds | R8 on by default | New in the SDK 58 template. Libraries that use reflection may need keep rules |
| iOS app startup | Scene-based lifecycle | Needed for the iOS 27 SDK. Bare apps migrate the app delegate |

**Module choices (repo's table, adjusted).** Before each cohort, check every module against React Native Directory and run `npx expo-doctor`.

| Need | Repo's choice | Course choice | Note |
| --- | --- | --- | --- |
| Push notifications | `@react-native-firebase/messaging` | Same | Used in Module 10 and the capstone |
| Secure storage | `react-native-keychain` | Same | Tokens and secrets |
| Plain storage | AsyncStorage | Same | Settings and small data |
| Backend | Firebase (Supabase as alternative) | Firebase | Auth, Firestore, Messaging |
| Maps | `react-native-maps` | Same | Capstone should-have |
| Camera | `react-native-vision-camera` | Same, only if needed | Boarding-pass scan is a could-have |
| Payments | `react-native-stripe` | `@stripe/stripe-react-native` | Official Stripe package. Test mode only |
| Location | `react-native-geolocation-service` | Open decision | See Section 13 |
| Local database | `react-native-sqlite-storage` | Not used | Firestore offline persistence covers the course needs |
| Icons | `react-native-vector-icons` | Same | Check the current install steps when you pin the version |
| Navigation | React Navigation | Same | Expo Router is not used |
| State | Zustand (plus Context) | Same | |
| Server state | React Query | TanStack Query | |
| UI kit | React Native Paper | Same | |
| Testing | Jest, Testing Library, Detox | Jest, Testing Library, plus Detox or Maestro | See Section 13 |
| Crash reporting | Sentry or Crashlytics | Same | |

## 12. Where This Differs From the Repo, and Why

*Updated October 22: two rows below (EAS Build and Expo Go) were corrected after re-reading the
repo's own `docs/expo-hybrid-approach.md` and `docs/deployment-guide.md` directly — they turned out
to be a closer match to the repo than the original draft assumed, not a divergence from it.*

| Repo says | This curriculum | Why |
| --- | --- | --- |
| Debug with Flipper | React Native DevTools | Flipper is no longer the default debugger in current React Native. Confirm before the cohort |
| EAS Update for over-the-air JS updates (the repo's actual OTA choice, per its deployment guide) | Discussion only | Keeping OTA out of scope keeps the release model simple for a 4-week course — build/submit is EAS, OTA is a separate decision a program owner can add later |
| `react-native-geolocation-service` | Open decision | A third-party summary of Expo's New Architecture guide lists `expo-location` as the swap for this library. Check Expo's own page before the cohort |
| `react-native-stripe` | `@stripe/stripe-react-native` | This is the official Stripe package, and it appears in the Expo SDK 58 list of third-party libraries |
| React Navigation 6 | Current stable major | Pin whatever is current when the cohort starts |
| Aviation Stack API for flight data | Seeded Firestore data | Free-tier limits would slow a 2-week build. Real data stays optional |
| OneSignal listed in the capstone stack | Firebase Cloud Messaging only | The repo's other weeks already use Firebase messaging. One push system is simpler |
| Voice, chat, Live Activities, geofencing, A/B tests and more | Cut | They do not fit in 4 weeks |

Some packages named in repo Weeks 3–8 (for example `react-native-image-cache`, `react-native-accessibility`, `react-native-background-job` and `react-native-background-sync`) were not checked. They are either cut from this version or replaced.

## 13. Open Decisions Before the First Cohort

1. **Node.js version.** 24 LTS or 26. Pin one per cohort.
2. **Xcode version.** 26.4 is the listed minimum. Expo SDK 58 is built for iOS 27, so decide whether the cohort uses Xcode 27. Test the whole course on the chosen version first.
3. **Starter template.** Until the SDK 58 Expo Go reaches the stores, `npx create-expo-app` creates SDK 57 projects. Confirm which SDK the `bare-minimum` template installs. If it is not SDK 58, use `init` plus `install-expo-modules`.
4. **Location library.** Use `expo-location` as the one Expo exception, or choose another maintained library. Only the could-have features need it.
5. **Image caching.** The repo names `react-native-image-cache`. Pick a maintained option, for example `expo-image`, which works in any React Native app.
6. **End-to-end tool.** Detox (the repo's choice) or Maestro (faster to set up). Pick one per cohort.
7. **Store accounts.** Choose one: the instructor owns the Apple and Google accounts and invites each engineer, or each engineer uses their own. If neither is possible, change Workshop D to signed ad hoc and local release builds, and the capstone gate to a signed build running on a device.
8. **Firebase setup.** One Firebase project per environment per team, or a shared set for the cohort. Decide who owns billing alerts.
9. **Hardware.** EAS Build builds iOS in the cloud, so a Mac isn't strictly required for iOS builds — but one is still useful for the simulator and local debugging. Either way, plan at least one real iPhone and one Android phone per team (push needs real iOS devices).
10. **Capstone brief.** Keep AirlineBooker Pro or choose one of the repo's other templates.

## 14. Sources

- Repo: `strat-training/bare-workflow-blueprint` (`README.md`, `week-01-hybrid`, `week-02-hybrid`, `week-03-04` to `week-09-10`, `capstone-projects`, `resources`, `docs`)
- [Expo SDK 58 changelog](https://expo.dev/changelog/sdk-58)
- [Expo SDK 58 reference and version table](https://docs.expo.dev/versions/v58.0.0)
- [React Native 0.88 release post](https://reactnative.dev/blog/2026/10/19/react-native-0.88)
- [React Native 0.87 release post](https://reactnative.dev/blog/2026/08/11/react-native-0.87)
- [Apple upcoming SDK requirements](https://www.developer.apple.com/news/upcoming-requirements/)
- [Google Play target API level requirements](https://support.google.com/googleplay/android-developer/answer/11926878?hl=en-419)
- [React Native New Architecture guide summary (newly.app)](https://newly.app/guides/hermes-new-architecture)
- `strat-training/bare-workflow-blueprint`: `docs/expo-hybrid-approach.md` and `docs/deployment-guide.md` (re-read October 22, 2026 directly from the repo to verify the EAS Build/Expo Go/EAS Update claims above)
