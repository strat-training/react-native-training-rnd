# M11 — AirlineBooker Pro (Team Capstone)

**Weeks 3–4 · 10 days · 40 hours, including four workshops**

## Builds on

Everything, M01 through M10. There is no reference solution for this stage — your own
`write-up-template.md` files, especially from M03 (variants and release builds), M06 (Firebase and
security rules), M07–M08 (state, sync and offline), M09 (UI and performance) and M10 (push), are
your material now. Re-read them before you start.

## Objective

Work as a team on one codebase through pull requests and code review, design a clean app structure
and hold it under time pressure, and ship signed release candidates for both platforms.

## The brief

**AirlineBooker Pro:** users sign in, search flights, pick one, enter passenger details, book it and
see their bookings. Flights come from a seeded Firestore collection, not a live flight API, so
free-tier limits don't slow the team down.

## Scope tiers

| Tier | Features |
| --- | --- |
| **Must have** | Sign-up and sign-in with an auth-guarded navigation flow. Flight search with filters (from, to, date, passengers) and a results list. Flight detail, passenger form and a booking saved to Firestore. "My Bookings" that also opens offline. A push notification on booking confirmation that opens the booking. Dev, Staging and Prod variants. Unit and component tests plus one end-to-end flow. Signed iOS and Android release candidates in TestFlight and the Play internal track |
| **Should have** | Seat selection. Payment with Stripe in test mode. A map of the airport or destination. Crash reporting. An accessibility and performance pass |
| **Could have** | Biometric unlock. Haptic feedback. Price alerts. Boarding-pass scan with the camera |

Work the tiers in order. Must-haves are the pass gate; should-haves and could-haves are where a
team spends whatever time is left. How far past must-have your team is expected to reach scales
with team size — see Team setup below.

## Team setup

Team size scales with your cohort — anywhere from a single learner working solo up to 5. Roles
rotate every two days across however many of these five functions your team size supports: tech
lead, release owner, UI owner, data and sync owner, quality owner. A pair might split tech
lead/release owner from UI/data/quality between them; a solo capstone holds all five and rotates
focus across them instead of rotating people between them. Every change still goes through a pull
request — a solo capstone gets review from another team or the trainer instead of a teammate.

Scope expectations scale the same way: a solo capstone is scored against the must-have tier only;
teams of 2–3 are expected to reach into should-haves; teams of 4–5 are expected to get through some
could-haves too. Confirm your team's size and which scope floor applies with your trainer before
Day 1.

## Stack constraints

Same pins as M01–M10: React Native 0.88, Expo SDK 58, React 19.3.0, Node 24 LTS, New Architecture
always on, TypeScript strict throughout. React Navigation, Zustand, Context, TanStack Query,
Firebase (Auth, Firestore, Messaging), `react-native-keychain`, Jest and React Native Testing
Library. An end-to-end tool and a maps library are needed for the must-have and should-have rows
below.

## Resolved: Firebase per team, per environment

Each team gets its own Firebase project per environment (Dev, Staging, Prod) for the capstone —
distinct from the personal project each of you made in M06. Agree as a team, on Day 1, who owns
billing alerts for the team's projects.

## Resolved: push and payment need a small server, and you own writing it

The source plan has no server for push and payments — Module 10's push came from a local script, and
Stripe normally needs a server to start a payment. For the capstone, each team runs **one small Node
service on a laptop**, used only for demos: it watches new bookings in Firestore and sends the
booking-confirmation push. If your team takes on the Stripe should-have, give it a payment stub
rather than a real charge flow. Designing and building this service is part of the capstone, not a
given — the architecture is yours to work out.

## Resolved: releases go through EAS Build and EAS Submit

Same tool you've used since Week 1: `eas build --profile production` for both platforms, then
`eas submit` to get the build into TestFlight and the Play internal track. Native folders stay
committed, same as every prior module — EAS still builds from them, it just does the
certificate/signing/upload work for you instead of you doing it by hand in Xcode and Android
Studio. A team that specifically wants the by-hand Xcode/Gradle path instead may choose it — ask
your trainer — but it isn't the default, and Workshop D below teaches the EAS path first.

## Resolved: secrets

Session tokens go in Keychain. Stripe runs in test mode only, if your team takes it on. The Firebase
Admin key for your push-sending service is never committed — agree as a team on Day 1 how it's
distributed and kept out of Git.

## End-to-end tool

Use Maestro for the one end-to-end flow (login, search, book) — it's faster to stand up than the
alternative, and Workshop B only gives you two hours. If your trainer tells you this cohort is using
a different tool, follow that instead.

## Schedule

| Day | Focus | Exit goal |
| --- | --- | --- |
| 1 | Kickoff and **Workshop A: Architecture** | Architecture decisions written down. Repo, CI (lint, type-check, tests), variants, Firebase projects and seed data ready. Work split into vertical slices |
| 2 | Auth and navigation | Sign-up, sign-in, secure session, auth-guarded navigation |
| 3 | Flight search | Search form, filters and a fast results list |
| 4 | Flight detail and booking | Passenger form, booking saved, My Bookings screen |
| 5 | Integration, mid-point demo and **Workshop B: Testing** | Demo to instructors, first round of code review, tests in CI |
| 6 | **Workshop D, part 1: Release with EAS** (2 hours), then payments or seat selection | First signed skeleton build in TestFlight and the Play internal track |
| 7 | Offline and push | My Bookings works offline, booking-confirmation push opens the booking |
| 8 | Maps, could-haves and **Workshop C: Performance and crash reporting** | Release-mode profile, crash reports with readable traces |
| 9 | **Workshop D, part 2: Release build** (2 hours), end-to-end tests and hardening | Tests green, accessibility pass, release branch cut |
| 10 | Demo and retro | Signed builds installed by testers from both store tracks |

**Workshop A: Architecture (Day 1)** — clean architecture and separation of concerns, folder layout
and import rules, custom hooks, Zustand with Context, error boundaries, short architecture decision
records.

**Workshop B: Testing (Day 5)** — Jest and React Native Testing Library, mocking native modules and
Firebase, what to test (auth, booking flow, offline cases, error cases), the one end-to-end flow,
and CI on GitHub Actions for lint, type-check and unit tests.

**Workshop C: Performance and Crash Reporting (Day 8)** — profiling with React Native DevTools,
Xcode Instruments and Android Studio Profiler; list tuning, image loading, startup time, bundle
size; crash and error reporting with Sentry or Firebase Crashlytics, including dSYM and R8 mapping
uploads.

**Workshop D: Build and Deploy with EAS (Days 6 and 9, 2 hours each)** — Apple Developer team roles
(EAS can manage credentials for you, or you can supply your own); `eas.json` build profiles;
`eas build --profile production` for both platforms; `eas submit` to App Store Connect/TestFlight
and the Play internal track; version/build numbering, release notes; a release checklist and a
rollback process. If your team chooses the by-hand path instead: manual certificates and
provisioning profiles, archiving with Xcode or `xcodebuild`, Android keystores and
`./gradlew bundleRelease` — ask your trainer for that track's checklist.

## Deliverable

**A working AirlineBooker Pro with every must-have feature in place, signed iOS and Android release
candidates installable by a tester from TestFlight and the Play internal track, and a 10-minute team
demo.**

## Lab

*Goal: ship a real multi-person app end to end — architecture, features, tests, a release through
EAS, and a team that can demo it under questions.*

**You do, as a team.**

1. Day 1 — run Workshop A, write your architecture decisions down, stand up the repo, CI, variants,
   Firebase projects and seed data, and split the must-have work into vertical slices.
2. Days 2–4 — build auth, flight search, flight detail and booking against the must-have list.
3. Day 5 — integrate, run the mid-point demo, and run Workshop B to get tests into CI.
4. Day 6 — run Workshop D part 1 and get a signed skeleton build into TestFlight and the Play
   internal track, then pick up a should-have.
5. Day 7 — build offline support for My Bookings and the booking-confirmation push, including your
   team's push-sending service.
6. Day 8 — pick up maps or a could-have, and run Workshop C to profile and wire up crash reporting.
7. Day 9 — run Workshop D part 2, finish the end-to-end test, harden the release branch.
8. Day 10 — finalize signed builds, demo to the room, and run your retro.

**You build and capture.** Every must-have feature working, both signed release candidates installed
by a tester from the store tracks, and your rubric self-score with evidence for each row.

## Rubric (100 points, 70+ passes)

| Area | Points |
| --- | --- |
| Architecture and code quality | 20 |
| Working features, including offline and push | 20 |
| Native build and release ownership (via EAS, or by hand if your team chose that path) | 20 |
| Tests and quality tooling | 15 |
| Teamwork and code review | 15 |
| Demo and retro | 10 |

**To pass:** 70% overall, every must-have feature working, and signed release candidates for both
platforms.

**For a solo capstone or a pair**, the Teamwork and code review row is judged on your pull-request
discipline and the quality of review you get from another team or your trainer, not on team
dynamics a 1–2 person team doesn't have.

## Definition of done

- [ ] Every must-have feature works.
- [ ] A tester installs both signed builds from the store tracks.
- [ ] The team delivers a 10-minute demo plus Q&A.
- [ ] The rubric scores 70 or more out of 100.

## Logistics

- **Store accounts.** Confirm with your program owner, before Week 1: whether your team uses
  instructor-owned Apple/Google accounts (with each of you invited) or your own, and settle Apple
  account access early since M10 also needs it. If no store accounts exist for this cohort, confirm
  the fallback release gate with your trainer before Day 6 — the default fallback is a signed build
  installed and running on a device, without the store tracks.
- **Hardware.** EAS Build builds iOS in the cloud, so your team doesn't need a Mac for that — but
  you'll still want one for the Xcode simulator and local debugging, and push needs at least one
  real iPhone regardless. Confirm your team's Mac and real-device pool with your trainer.
- **Alternate capstone brief.** AirlineBooker Pro is this cohort's brief. If your program owner
  swaps in a different one, the same scope-tier structure applies — ask for the tier list before you
  start.
