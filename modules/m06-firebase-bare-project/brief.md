# M06 — Firebase on a Bare Project

**Week 2 · Day 1 · 4 hours**

## Builds on

[M05](../m05-dev-workflow-professional-structure/write-up-template.md) — the project structure and
storage-service pattern from Week 1 carry over, but this starts a new project: the **Full-Stack
To-Do App**.

## Objective

Connect a bare React Native app to Firebase, sign users in and out, and protect their data with
security rules.

## Scope

- React Native Firebase modules: `app`, `auth`, `firestore`, `messaging`.
- Config files and where they go: `GoogleService-Info.plist` in `ios/`, `google-services.json` in
  `android/app/`, plus the Gradle and Xcode changes each one needs.
- One Firebase app per environment (Dev, Staging, Prod), wired to the build variants you already
  built in M03.
- Firebase Auth with email and password.
- A Firestore data model for to-dos.
- Security rules — specifically, rules that let each signed-in user read and write only their own
  documents, not the open "any signed-in user can touch anything" rule a starter guide would show
  you.
- Firebase's free-tier limits. Supabase as a concept-only alternative backend — not built in this
  course.

## Stack constraints

- Same pins as M01–M05. React Native Firebase, pinned in your lockfile.

## Resolved: one Firebase project per learner

For this individual module, each learner creates their own Firebase project (Dev/Staging/Prod apps
within it). This is separate from the capstone's team-level Firebase setup in M11.

## Deliverable

**The To-Do App's sign-up, sign-in and sign-out flow working on both platforms against your own
Firebase project, with security rules that provably stop one user from reading another's data.**

## Lab

*Goal: wire up a real backend and prove, not just assert, that your security rules work.*

**You do.**

1. Create your Firebase project (or its three environment apps, if you're carrying the variants
   forward) and install the React Native Firebase modules.
2. Add the platform config files and wire the Gradle/Xcode changes they need.
3. Build sign-up, sign-in and sign-out screens.
4. Design the Firestore data model for to-dos.
5. Write security rules so each user can read and write only their own to-dos.
6. Prove it: write a rules test (or a manual two-account test) that shows user B cannot read user
   A's data.

**You build and capture.** Auth working on both platforms, and the evidence that your rules test
actually failed before you tightened the rules and passed after.

## Definition of done

- [ ] Auth works on both platforms.
- [ ] A rules test (or equivalent two-account proof) shows user B cannot read user A's data.
