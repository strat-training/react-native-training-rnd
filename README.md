# React Native Bare Workflow Training

This repo holds the Build-to-Teach version of the React Native Bare Workflow curriculum: ten
individual-work stages in `modules/` (M01–M10), followed by a team capstone (M11). The format is
different on purpose: instead of being taught the material, the senior developer builds toward each
stage's deliverable from a brief, and writes up how they did it as they go. The write-up is what
ends up teaching the next cohort.

A note on words: in this repo, "trainee" means **the senior developer working through a stage** —
not the junior developer who, in a later cohort, learns from the finished write-up that senior
developer produces. See `.claude/commands/trainee-task-planner.md` if you need the full three-role
breakdown (EM, senior developer, junior/end-learner).

## What is in this repository

| Path | What it holds |
| --- | --- |
| `modules/` | The ten stage folders (M01–M10), each with a brief and a write-up template |
| `modules/m11-airlinebooker-capstone/` | The team capstone, with its own brief and write-up template |
| `docs/` | The PRD, the Solution Design, and the Build-to-Teach framework this repo implements |

Each stage folder also gets a `tasks.md`, generated from its `brief.md` with `/trainee-task-planner`
— an ordered checklist mirroring the brief. It isn't written by hand and isn't included until it's
generated for that stage.

## Ground rules (every stage)

- **Native folders stay committed, always.** `ios/` and `android/` are committed to Git — that's
  the "bare workflow" part this program keeps. Building and running stays Expo-first throughout:
  Expo Go for pure-JS screens before Module 2 links native modules, dev builds after that, and EAS
  Build as the build tool all the way through the capstone's release candidates. A by-hand
  Xcode/Gradle build is something a team can choose instead in the capstone if they want the extra
  depth, but it's never the required path. EAS Update (OTA) stays out of scope everywhere.
- **Free tiers first.** Firebase free tier, GitHub Actions on public repos, Stripe test mode. The
  only unavoidable costs are the Apple Developer Program and Google Play Console accounts.
- **Pinned versions for the whole cohort:** React Native 0.88, Expo SDK 58, React 19.3.0, Node.js 24
  LTS, New Architecture always on, Xcode 26.4+, Android `compileSdk` 37 / `targetSdk` 36. Your
  trainer re-verifies these are still current immediately before the cohort starts — the stack moves
  fast, and the program freezes exact versions two weeks before Day 1.
- **TypeScript throughout**, in the Strict TypeScript API style, from Module 1 onward.
- **Git/GitHub workflow throughout:** a starter repo per project, feature branches, pull requests,
  and a Git tag at the start and end of every module so you can reset to a known state if you fall
  behind.
- **Install SDK-aligned libraries with `npx expo install`**, not by guessing a version.
- **State has three homes, program-wide:** Zustand for client state, Context for theme and the auth
  session, TanStack Query for server data.

## How a stage works

1. **Your trainer hands you the brief.** Each stage's `brief.md` says what to build and how you
   will know it is done: objective, scope, stack constraints, the named deliverable, a lab, and a
   definition of done. It contains no lesson, no steps, no code and no solutions. How to build it is
   yours to work out.
2. **You build and write up the stage together.** Fill in `write-up-template.md` while you build,
   not after it already works. The lab's "you build and capture" section is your deliverable; your
   write-up is the teaching content — write it for someone who will follow it with no trainer to
   ask.
3. **Your trainer reviews both together.** When you reach the definition of done, bring the working
   system and the write-up to your checkpoint. The question is not only "does it work?" but "could
   someone else learn from this?"
4. **You revise.** Fix what the review finds, in both the build and the write-up, before starting
   the next stage.
5. **The finished pair goes into the content library.** An accepted stage is the build plus its
   write-up. Your trainer decides what carries into the next cohort's plan.

Review happens at the end of every stage, not just at the end of the course — see
`docs/build-to-teach-framework.md` for the full reasoning behind this.

## What is in each stage folder

| File | Who writes it | Purpose |
| --- | --- | --- |
| `brief.md` | Your trainer | Objective, scope, stack constraints, the deliverable, a lab, and a definition of done. No answers. Do not edit it. |
| `write-up-template.md` | You | Blank at first; filled in as you build, not after. |
| `tasks.md` | Generated from `brief.md` via `/trainee-task-planner` | An ordered checklist mirroring the brief. You tick the boxes; it holds no answers and no steps you weren't already told. |

Your React Native code lives outside this repository, in your own GitHub repo (set up in M01). Link
it from the header of your write-up. The capstone folder has the same files, at team scope.

## Stages

| Stage | Title | Week | Hours | Theme | Leaves behind |
| --- | --- | --- | --- | --- | --- |
| [M01](modules/m01-toolchain-hybrid-project-setup/brief.md) | Toolchain and Hybrid Project Setup | 1 | 4 | Native toolchain, the bare-workflow starter project | `PersonalProfileApp` skeleton |
| [M02](modules/m02-community-modules-native-linking/brief.md) | Community Modules and Native Linking | 1 | 4 | Hand-linking native modules, a lock-in audit | Three linked modules + audit |
| [M03](modules/m03-ios-android-project-internals/brief.md) | iOS and Android Project Basics | 1 | 5 | App identity, EAS build profiles | Dev/Staging/Prod EAS build profiles |
| [M04](modules/m04-core-components-layout-navigation/brief.md) | Core Components, Layout and Navigation | 1 | 5 | Screens, navigation, accessibility | Profile, Edit Profile, Settings screens + the accessibility checklist (reused in M09, M11) |
| [M05](modules/m05-dev-workflow-professional-structure/brief.md) | Dev Workflow and Professional Structure | 1 | 2 | Debug/build loop, project structure | Restructured app + storage service |
| [M06](modules/m06-firebase-bare-project/brief.md) | Firebase on a Bare Project | 2 | 4 | Auth, Firestore, security rules | Auth'd `To-Do App` skeleton |
| [M07](modules/m07-state-and-server-data/brief.md) | State and Server Data | 2 | 4 | Zustand, Context, TanStack Query, optimistic updates | To-do CRUD + service layer |
| [M08](modules/m08-realtime-sync-offline/brief.md) | Real-Time Sync and Offline | 2 | 4 | Snapshot listeners, offline persistence | Synced, offline-safe to-do list |
| [M09](modules/m09-professional-ui-core-components/brief.md) | Professional UI and Core Components | 2 | 4 | Paper UI, list performance, accessibility | Polished, perf-tuned to-do app |
| [M10](modules/m10-push-notifications-fcm/brief.md) | Push Notifications with FCM | 2 | 4 | FCM, permissions, a local push-sending script | Push-enabled to-do app (handed off to M11) |
| [M11](modules/m11-airlinebooker-capstone/brief.md) | AirlineBooker Pro (team capstone) | 3–4 | 40 | Team build, architecture, release with EAS | — (terminal stage) |

Work the stages in order. Week 1 builds the Personal Profile App (M01–M05); Week 2 builds the
Full-Stack To-Do App (M06–M10) on new Firebase/state/sync/UI/push foundations; Weeks 3–4 are the
team capstone (M11), which draws on all ten prior write-ups rather than extending either project
directly. Folder names are descriptive; each brief refers to other stages by module ID (M01–M11).

## Assessment

- Every module ends in a pass/fail checkpoint (see that stage's `brief.md`) — together worth 25% of
  the overall grade.
- The two individual projects — the Personal Profile App (end of Week 1) and the Full-Stack To-Do
  App (end of Week 2) — are worth 25%, scored against their own module checkpoints plus code
  quality.
- The capstone (M11) is worth 50%: the 100-point rubric in `modules/m11-airlinebooker-capstone/brief.md`
  (70+ passes), plus individual contribution from pull requests, judged by your trainer rather than
  counted.

## Open decisions before the first cohort

These are cohort-specific and this repo can't settle them in advance — confirm each with your
program owner before the dates noted:

- **Store accounts** (instructor-owned vs. learner-owned vs. none) — before Week 1, since M10 needs
  Apple account access in Week 2, not only at the capstone's deploy workshop.
- **Hardware** — a real-device pool for push (M10) and the capstone (at least one iPhone and one
  Android phone per team), sized from cohort size. EAS Build builds iOS in the cloud, so a Mac pool
  is no longer a hard requirement.
- **Firebase ownership and billing alerts** — per-learner in M06, per-team-per-environment in M11.
- **End-to-end tool** (Maestro is the program default; confirm if this cohort uses something else).
- **Exact Xcode/Node point versions** — re-verified against the pinned baseline immediately before
  freeze, two weeks ahead of Day 1.

## Sources

- `docs/arch-docs/React Native Bare Workflow Curriculum — Solution Design.md` — the design this
  module set implements, including its full risk list and decision matrix.
- `docs/prd/react-native-bare-workflow-curriculum.md` — the source curriculum this design is built
  from.
- `docs/build-to-teach-framework.md` — the mechanism behind brief → build → write-up → review.
