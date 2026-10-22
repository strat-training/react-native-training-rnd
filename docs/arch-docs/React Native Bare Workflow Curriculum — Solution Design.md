# React Native Bare Workflow Curriculum — Solution Design

Oct 21, 2026 · @Ryan Angelo

## Overview and Purpose

This design turns the 4-week React Native bare workflow curriculum into a plan for building and running the course. It covers the lab repos, the reference app, the release pipeline and the delivery setup.

The source curriculum (draft of October 21, 2026, revised October 22) has one goal: senior engineers finish able to build, test and ship signed iOS and Android apps using EAS Build and EAS Submit, with a by-hand Xcode/Gradle path available for teams that want the extra depth. It runs about 80 hours, with 11 modules and three projects: a Personal Profile App (Week 1), a Full-Stack To-Do App (Week 2) and a team capstone, AirlineBooker Pro (Weeks 3–4).

**Design principles taken from the source**

- **Bare workflow.** The `ios/` and `android/` folders belong to the learner and are committed to Git.
- **Expo Hybrid.** Use Expo's tooling (Expo Go, dev builds, EAS Build) for a fast developer loop and a simple release process, and community modules for core features instead of locking into Expo's managed SDK.
- **EAS-first builds.** EAS Build and EAS Submit are the course's build and release tool throughout, including the capstone's signed release candidates — the source repo's own `docs/deployment-guide.md` recommends this path. A by-hand Xcode/Gradle release stays available as an optional deeper path.
- **Free tiers first.** Firebase free tier, GitHub Actions on public repos, Stripe test mode and EAS Build's free tier. The only forced costs are the Apple and Google store accounts.
- **Scope in tiers.** The capstone uses must-have, should-have and could-have lists so two weeks stays realistic.

**Success measures.** The source sets pass rules only: 70% overall, all must-have features working, and signed release candidates for both platforms. It gives no completion-rate or time-to-competency targets. *Proposed:* ask the program owner whether to track them.

**How to read this document.** Anything taken from the source is stated plainly. Anything the source does not say is marked *Proposed* and collected in the open decisions section for the program owner to confirm.

**October 22 revision.** The original draft of this design assumed the source repo avoided EAS Build and Expo Go entirely, based on a surface read of its top-level README. A direct read of the repo's own `docs/expo-hybrid-approach.md` and `docs/deployment-guide.md` showed the opposite: the repo recommends EAS Build, keeps Expo Go for JS-only testing, and never teaches a deep by-hand signing path. This design, the PRD and all 11 modules were revised to match — see the updated rows in Curriculum and Module Mapping, Risks Gaps and Open Decisions, and the Decision Status Matrix below.

## Audience and Prerequisites

The course is for senior engineers who already build software professionally and want full control of iOS and Android builds. No mobile experience is needed.

| Prerequisite (from the source) | Why it matters in this design |
| --- | --- |
| JavaScript or TypeScript and modern React (hooks, components, state) | Modules 4–9 teach mobile APIs, not React basics |
| Git, terminal and pull requests every day | The capstone runs on pull requests with one reviewer per change |
| REST APIs and token-based auth | Needed for Firebase Auth and the secure session in the capstone |
| A Mac helps but isn't required for iOS work | EAS Build builds iOS in the cloud, so Windows and Linux learners can ship signed iOS release candidates too. A Mac is still useful for the simulator and local debugging |
| Swift or Kotlin reading (helpful, not required) | Module 3 has learners skim the generated native files briefly; no hand-editing of Swift/Kotlin is required |

**What a graduate can do.** The source lists nine outcomes. They group into four areas: set up the native toolchains and projects (outcomes 1–4), build accessible full-stack screens (5–6), test and profile (7), and make signed releases and work in a team (8–9).

**Proposed: download before Day 1.** Module 1 teaches the toolchain setup, so learners should not pre-install it. They can still download the Xcode and Android Studio installers a week early, so the 4 hours go to learning and not waiting on large downloads.

**Gap: cohort size.** The source does not give one. Every 4–5 learners adds a team that needs its own devices and review time, so the size drives the Mac, phone and instructor counts. This is raised again in the open decisions.

## Technology Stack and Version Baseline

The baseline is Expo SDK 58 on React Native 0.88, with the New Architecture always on and CocoaPods as the iOS default. Most of the source's version table checks out as of October 21, 2026. The last column says what I could and could not confirm.

| Item | Course choice (source) | What I checked |
| --- | --- | --- |
| React Native | 0.88 | Confirmed. The [release post](https://reactnative.dev/blog/2026/10/19/react-native-0.88) says no user-facing breaking changes |
| Expo SDK | 58 | The [Expo docs table](https://docs.expo.dev/versions/v58.0.0) pairs SDK 58 with React Native 0.88. I could not confirm the stable release date; the pages I opened cover the September 15 beta |
| React | 19.3.0 | Confirmed in the same Expo docs table |
| Node.js | 24 LTS | The Expo docs list 22.13.x as the minimum. The source's "24.3+ and 26+" range was not confirmed |
| Xcode and iOS | Xcode 26.4+, iOS 16.4+ | Confirmed in the Expo docs. [Expo's beta post](https://expo.dev/changelog/sdk-58-beta) says SDK 58 is built for iOS 27 and that Xcode 27 replaces Simulator.app with Device Hub |
| Android | compileSdk 37, targetSdk 36 | Confirmed in the Expo docs. The Google Play deadline was not re-checked |
| iOS startup | Scene-based lifecycle | [React Native 0.88](https://reactnative.dev/blog/2026/10/19/react-native-0.88) adds scene support and keeps the app delegate path. Per a [weekly digest](https://releases.sh/collections/frontend-frameworks/digest/2026-09-14), Expo SDK 58 moves apps to scenes, so projects that edit `AppDelegate.swift` must migrate |
| Swift Package Manager | Not covered | Still experimental and opt-in in 0.88. CocoaPods stays fully supported and is what EAS Build uses by default, so this version of the course doesn't teach SPM at all (see Module 3's lighter scope) |
| React Navigation | "Current stable major" | *Proposed:* pin version 7. Version 8 was still pre-release in the [July 2026 progress report](https://reactnavigation.org/blog/2026/07/08/react-navigation-8.0-july-progress) |

**Libraries that match the SDK.** The SDK 58 docs list bundled versions for AsyncStorage, NetInfo, Gesture Handler, Reanimated, Safe Area Context, Screens, Maps and the Stripe package. *Proposed:* install these with `npx expo install` so learners never choose a version.

**Libraries with no pinned version.** The source gives no versions for React Native Firebase, React Native Paper, Zustand, TanStack Query, Zod, Keychain, vector icons, the end-to-end tool or the crash reporter. *Proposed:* pin each in the starter repo lockfile.

**Freeze date.** The source says to pin exact versions per cohort and check again before each run. *Proposed:* freeze the stack two weeks before Day 1, then run the whole course once on that frozen stack.

## Program Timeline

The course runs 20 days of about 4 hours each: two solo weeks, then two team weeks that end in signed builds from both store tracks.

&#91;embedded content: program timeline · 4 weeks, 4 workshops, 4 gates\]

Weeks 1 and 2 hold five modules each, 20 hours per week. Weeks 3 and 4 are the 40-hour capstone, with a mid-point demo on Day 5 and four workshops: A (architecture), B (testing), C (performance and crash reporting) and D (build and deploy with EAS). The workshops take 12 of the 40 hours, and Workshop D is 6 of those.

**Proposed day split for Week 1.** The source's modules run 4, 4, 5, 5 and 2 hours, which does not fit five 4-hour days. In the drawing, Module 3 spills one hour into Day 4 and Module 4 spills two hours into Day 5.

**Proposed Workshop D hours.** The source says 6 hours across Days 6, 9 and 10, but its plan table shows nothing on Day 9. The drawing puts 2 hours on each of those three days.

## Curriculum and Module Mapping

Each of the 11 modules ends in one pass-or-fail checkpoint, and this design uses that checkpoint as the module's definition of done. Every module follows the same pattern: objectives, topics, a lab and a checkpoint. A 4-hour module is about 60 minutes of talk, 144 minutes of lab and 36 minutes of checkpoint (25%, 60% and 15%).

| # | Module | Hours | Checkpoint (pass test) | Design note |
| --- | --- | --- | --- | --- |
| 1 | Toolchain and Hybrid Project Setup | 4 | A fresh clone builds and runs on both platforms using only the README | *Proposed:* one script that plants the three setup faults (wrong Node version, missing Pod install, bad `ANDROID_HOME`), so every learner gets the same ones |
| 2 | Community Modules and Native Linking | 4 | Lock-in audit passes review and `npx expo-doctor` reports no errors | *Proposed:* give learners an audit template with one filled-in example row |
| 3 | iOS and Android Project Basics | 5 | Three EAS build profiles each build successfully and sit on one device, and the learner can point to where the bundle ID and version number land in the native folders | New in this version, but lightened on October 22 to match the source's own approach: app identity through EAS build profiles, not hand-edited Xcode schemes, Gradle flavors, a scene migration or an R8 fix |
| 4 | Core Components, Layout and Navigation | 5 | Data survives a restart, navigation works, and the accessibility checklist passes | The source names a checklist but does not supply it. *Proposed:* one short checklist reused in Modules 9 and 11 |
| 5 | Dev Workflow and Professional Structure | 2 | TypeScript and lint pass, and the app still runs after the folder move | The take-home bonus (build the same app with `react-native init`) is not scheduled |
| 6 | Firebase on a Bare Project | 4 | Auth works on both platforms, and a rules test shows user B cannot read user A's data | One Firebase project per environment, tied to the Module 3 variants |
| 7 | State and Server Data | 4 | A forced save failure rolls back the optimistic update and shows an error | Zod is used at the service edges |
| 8 | Real-Time Sync and Offline | 4 | An airplane-mode test script passes and both devices end with the same data | Needs two running devices per learner. Two simulators or emulators can stand in |
| 9 | Professional UI and Core Components | 4 | 2,000 to-dos scroll smoothly in a release build, and the accessibility checklist passes | Measure in a release build, not debug |
| 10 | Push Notifications with FCM | 4 | Works on a real iPhone and a real Android device, and the denied-permission path does not crash | Needs an Apple account for the push key in Week 2. See the risks section |
| 11 | AirlineBooker Pro (team capstone) | 40 | Teams demo a working app, and a tester installs both signed builds from the store tracks | Covered in the reference application section |

**What changed from the 10-week repo.** Weeks 1–2 of the repo are kept in full, plus two additions: Module 3 (native project basics via EAS build profiles) and Module 10 (push, moved up from repo Weeks 7–8). Repo Weeks 3–4 become the capstone. Repo Weeks 5–10 are cut down by tier: testing, push, offline and store deployment are must-haves, and voice search, chat, Live Activities and geofencing are cut.

**Stretch lab.** A small native module in Swift and Kotlin with the Expo Modules API is not scheduled. Whether it gets a short demo is an open decision.

## Reference and Capstone Application Design

AirlineBooker Pro is built in layers, with a service layer between the screens and Firebase, so a team of 4–5 can build vertical slices without tangling the code.

&#91;embedded content: AirlineBooker Pro architecture - 5 layers on the device, 2 services off it\]

Read the drawing from top to bottom. Screens use state, state calls the service layer, services call community native modules, and those modules are linked into the committed `ios/` and `android/` projects. Firebase and the push sender sit off the device.

**What gets built.** Users sign in, search flights, pick one, enter passenger details, book it and see their bookings. Flights come from a seeded Firestore collection, not the Aviation Stack API. The default brief can be swapped for another, but only this one has scope tiers.

| Tier | Features |
| --- | --- |
| Must have | Sign-up and sign-in with an auth-guarded flow. Flight search with filters. Flight detail, passenger form and a booking saved to Firestore. My Bookings that also opens offline. A push for booking confirmation that opens the booking. Dev, Staging and Prod variants. Unit and component tests plus one end-to-end flow. Signed iOS and Android release candidates in TestFlight and the Play internal track |
| Should have | Seat selection, Stripe payment in test mode, a map, crash reporting, and an accessibility and performance pass |
| Could have | Biometric unlock, haptic feedback, price alerts, boarding-pass scan with the camera |

**Design rules**

1. **State has three homes.** Zustand for client state, Context for theme and the auth session, TanStack Query for server data (source).
2. **Firebase stays behind the services.** *Proposed:* a lint rule fails the build if code outside `services/` imports Firebase. Workshop A already covers import rules, so teams can write this rule on Day 1.
3. **One environment, one Firebase project.** Dev, Staging and Prod each get their own app ID, name, icon and Firebase config files, so all three install side by side (source).
4. **Offline comes from Firestore.** Offline persistence and snapshot listeners keep My Bookings readable with no network, and NetInfo reports the connection state (source).
5. **Secrets stay out of Git.** Session tokens go in Keychain, and Stripe runs in test mode only (source). *Proposed:* the Firebase Admin key for the push sender is never committed.
6. **Releases go through EAS.** Native folders are committed; `eas build` and `eas submit` produce and upload signed release candidates to TestFlight and the Play internal track — matching the source's own recommended path. *Corrected October 22:* the original draft had this as "built by hand" and wrongly attributed it to the source; the source's deployment guide actually recommends EAS Build. A by-hand Xcode/Gradle path is available for teams that want it.

## Testing and Assessment Strategy

Learners are judged at three levels: module checkpoints, two individual projects and the capstone. The source's pass rule is clear, but four scoring details are missing and are listed below.

**How learners test their apps**

| Layer | Tool (from the source) | Where it appears | In CI |
| --- | --- | --- | --- |
| Unit and component tests | Jest and React Native Testing Library | Modules 7–9 and the capstone | Yes |
| Security rules test | Not named in the source | Module 6 | Not stated |
| Offline and sync | Airplane-mode test script | Module 8 | No, needs devices |
| End-to-end | Detox or Maestro (open decision) | Capstone Workshop B, one flow: login, search, book | No. The source CI covers lint, type-check and unit tests only |
| Performance | React Native DevTools, Xcode Instruments, Android Studio Profiler | Module 9 and Workshop C | No |
| Accessibility | Short checklist plus a screen reader pass | Modules 4 and 9, and the capstone | No |

**How learners are graded**

| Part | Weight | How it is judged |
| --- | --- | --- |
| Module checkpoints | 25% | Pass or fail per module, reviewed by the instructor |
| Individual projects | 25% | Personal Profile App (end of Week 1) and Full-Stack To-Do App (end of Week 2) |
| Capstone | 50% | Team rubric plus individual contribution from pull requests |

The capstone rubric is out of 100 points: architecture and code quality 20, working features including offline and push 20, native build and release ownership 20, tests and quality tooling 15, teamwork and code review 15, demo and retro 10. To pass, a learner needs 70% overall, every must-have feature working, and signed release candidates for both platforms.

**Gaps in the scoring**

1. **Checkpoint weight.** Pass or fail results count for 25%, but the source does not say how they turn into points. *Proposed:* each of the 11 checkpoints is worth an equal share (about 2.3 points), with one retry.
2. **Individual project rubric.** The two projects are worth 25% together, and the source gives no rubric. *Proposed:* score each against its module checkpoints plus code quality.
3. **Team versus individual.** The source does not say how the team rubric and pull request contribution combine. *Proposed:* treat pull requests as evidence for the instructor's judgment, not as a count, since counts are easy to game.
4. **Release gate without store accounts.** The pass rule needs signed release candidates, but open decision 7 offers a different gate if no store accounts exist. Both versions of the rule need to be written down before the cohort starts.

## Delivery Model

The course runs live for about 4 hours a day over 20 days: Weeks 1–2 are individual work, and Weeks 3–4 are a team capstone. The hardest part to deliver is not the teaching but the equipment: real phones and store accounts (EAS Build's cloud iOS builds take Macs mostly off this list — see below).

**Format**

- **Weeks 1–2.** Each learner works alone on a project, one module at a time, and the instructor reviews each checkpoint.
- **Weeks 3–4.** Teams, sized to the cohort — anywhere from a single learner solo up to 5 — work on one codebase. Roles rotate every two days across however many of five functions the team size supports: tech lead, release owner, UI owner, data and sync owner, and quality owner. Every change goes through a pull request with at least one reviewer (a solo capstone gets review from another team or the instructor). *Revised October 22:* scope expectations now scale with team size — solo is must-have only, 2–3 reaches should-haves, 4–5 reaches some could-haves.
- **Instructor touchpoints.** Checkpoint reviews, a mid-point demo on capstone Day 5, and a final demo and retro on Day 10. The source gives no instructor count or support hours.

**What each learner or team needs**

| Need | Who needs it | Notes |
| --- | --- | --- |
| Apple silicon Mac (helpful, not required) | Learners doing local iOS work | EAS Build builds iOS in the cloud, so Windows and Linux learners can still ship signed iOS release candidates. A Mac is still useful for the simulator and local debugging |
| Real iPhone and Android phone | At least one of each per team | Push needs real iOS devices. Module 10 is individual and in Week 2, so *Proposed:* plan a shared device pool for Week 2 as well |
| Apple Developer Program, $99 a year | Whoever signs and uploads iOS builds | Needed for TestFlight. Creating the push key in Module 10 also needs a paid Apple account (my reading; the source does not say so). Check the current price |
| Google Play Console, $25 one time | Whoever uploads Android builds | Needed for the internal testing track. Check the current price |
| Firebase projects (free tier) | One per environment per team, or shared by the cohort | Open decision 8, including who owns billing alerts |
| GitHub repos and Actions | Each team | The source lists Actions as free for public repos. *Proposed:* run CI on Linux runners for lint, type-check and unit tests only, so no iOS build runs in CI |

**Proposed repo layout.** Build on the existing `strat-training/bare-workflow-blueprint` repo as the source of truth, and add:

- A **course guide** with one page per module for learners and instructors.
- A **starter repo** for each project, with a Git tag at the start and end of every module so a learner who falls behind can reset to a known state.
- An instructor-only **solutions** branch per module.
- A **cohort kit**: the setup check script, the planted-fault script, the lock-in audit template, the accessibility checklist, the release checklist and the grading sheet.
- The **seed data** for the flight collection in Firestore, with a script to load it.

## Risks, Gaps and Open Decisions

I found nine gaps and risks in the source and this design. The first two matter most: the plan has no server for push and payments, and the Apple account is needed in Week 2, not only at the deploy workshop.

| # | Gap or risk | What the source says | Proposed handling |
| --- | --- | --- | --- |
| 1 | No server for push and payments | Module 10 sends push from a local Node script because Cloud Functions need a paid Firebase plan. The capstone needs a push on booking confirmation, and Stripe (a should-have) normally needs a server to start a payment. The source does not say where that code runs | One small Node service per team, run on a laptop for demos. It watches new bookings in Firestore and sends the push. Give teams a payment stub |
| 2 | Apple account needed in Week 2 | Module 10 needs a push key and a real iPhone in Week 2. Open decision 7 only covers Week 4 | Settle account access before Week 1, and invite learners to the instructor's Apple team before Module 10 |
| 3 | Module 3 was overloaded | *Resolved October 22.* The original 5-hour lab asked for three hand-made variants on two platforms, a scene migration and an R8 fix — heavier than the source itself ever asks for | Lightened to match the source: three EAS build profiles for Dev/Staging/Prod, no hand-edited Xcode schemes or Gradle flavors, no scene migration, no R8 fix |
| 4 | Module hours do not fit a 4-hour day | Week 1 modules run 4, 4, 5, 5 and 2 hours | Use the day split shown in the timeline section |
| 5 | Workshop D is missing from Day 9 | The workshop text says Days 6, 9 and 10. The plan table shows 2 hours on Day 6 and part 2 on Day 10, and nothing on Day 9 | 2 hours on Day 9 and 2 hours on Day 10 |
| 6 | The release gate depends on review time | The gate needs testers to install both builds from the store tracks | Use internal TestFlight groups and the Play internal track for the Day 10 gate. As far as I know, external TestFlight groups need a beta review first |
| 7 | Other capstone briefs have no scope tiers | The source says other briefs can be swapped in and "the same scope tiers apply", but only AirlineBooker Pro lists features per tier | Write tier lists for any brief before offering it |
| 8 | The stack moves fast | React Native plans to remove CocoaPods in a later release, and Expo ships a new SDK three times a year | Freeze before each cohort and review the course after each run |
| 9 | EAS free-tier build queue, with every team building through it | *New, from the October 22 revision.* A 4–5 person team all triggering `eas build` on the free tier can queue behind other builds, including other teams' | Budget build time into the Workshop D schedule rather than assuming instant builds; a paid EAS plan is a fallback if a cohort's queue times become a real problem |

The source's own 11 open decisions are tracked in the decision matrix that follows.

## Decision Status Matrix

Fourteen decisions need the program owner's sign-off: the source's 11 open decisions plus three this design adds. Each starts as Proposed. Change the status as decisions are made.

| # | Decision | From | Proposed position | Status |
| --- | --- | --- | --- | --- |
| 1 | Node.js version: 24 LTS or 26 | Source | Use 24 LTS. It is the source's course choice and above Expo's 22.13 minimum. I could not confirm 26 support. Pin one version per cohort | Proposed |
| 2 | Xcode version: 26.4 minimum, or 27 | Source | Stay on the latest 26.x unless a full run of the course on Xcode 27 passes before the freeze. Xcode 27 also replaces Simulator.app | Proposed |
| 3 | Starter template: does `bare-minimum` install SDK 58? | Source | Check at the freeze. If not, the trainer switches learners to `init` plus `install-expo-modules` instead (see Module 1's Logistics) | Proposed |
| 4 | Location library | Source | Use `expo-location`, which the SDK 58 docs list. Only could-have features need it. The docs also list a newer "Location (next)" page, so check which one to teach | Proposed |
| 5 | Image caching library | Source | Use `expo-image`, which the SDK 58 docs list | Proposed |
| 6 | End-to-end tool: Detox or Maestro | Source | Maestro. The source calls it faster to set up, and Workshop B is only 2 hours | Proposed |
| 7 | Store accounts: instructor-owned, learner-owned, or none | Source | Instructor-owned Apple and Google accounts with each learner invited. Keep the no-account fallback gate written down | Proposed |
| 8 | Firebase setup: per team or shared | Source | One project per environment per team for the capstone. Each learner makes their own in Module 6. The instructor owns billing alerts | Proposed |
| 9 | Hardware for Windows and Linux learners, and phones per team | Source | *Revised October 22:* EAS Build builds iOS in the cloud, so a Mac pool is no longer required for Windows/Linux learners to ship signed iOS builds — only a real-device pool (at least one iPhone and one Android phone per team) is, sized from the cohort size | Proposed |
| 10 | Capstone brief: AirlineBooker Pro or another | Source | Keep AirlineBooker Pro for the first cohort. It is the only brief with scope tiers | Proposed |
| 11 | Swift Package Manager and the native module lab | Source | *Resolved October 22:* cut entirely, not even a slide — EAS Build uses CocoaPods, and the lighter Module 3 no longer has room for a native-module stretch lab | Resolved |
| 12 | Where push and payment server code runs | Design | One small Node service per team, run on a laptop for demos | Proposed |
| 13 | Week 1 day split and Workshop D time on Day 9 | Design | Use the day split in the timeline section, and 2 hours of Workshop D on Day 9 | Proposed |
| 14 | Scoring details: checkpoint weights, project rubric, team versus individual, no-account gate | Design | Use the positions in the assessment section | Proposed |
