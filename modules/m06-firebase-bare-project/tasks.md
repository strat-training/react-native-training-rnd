# M06 Tasks — Firebase on a Bare Project

Connect a bare React Native app to Firebase, sign users in and out, and protect their data with
security rules.

> There is no solutions file for this stage. This checklist guides the work; it doesn't contain it.

## Setup

- [ ] Read this stage's `brief.md` fully.
- [ ] Research the React Native Firebase modules you'll need: `app`, `auth`, `firestore`,
      `messaging`.
- [ ] Research the platform config files (`GoogleService-Info.plist`, `google-services.json`) and
      the Gradle/Xcode wiring each needs.
- [ ] Research how to set up one Firebase app per environment and wire it to the Dev/Staging/Prod
      variants from M03.
- [ ] Research Firebase Auth with email and password.
- [ ] Research Firestore data modeling approaches for a to-dos collection.
- [ ] Research how Firestore security rules work, and what a default "any signed-in user can touch
      anything" rule looks like versus a locked-down one.
- [ ] Research Firebase's free-tier limits, and Supabase as a concept-only alternative backend.

## Build

- [ ] Create your Firebase project (or its three environment apps if carrying the variants forward)
      and install the React Native Firebase modules.
- [ ] Add the platform config files and wire the Gradle/Xcode changes they need.
- [ ] Build the sign-up screen.
- [ ] Build the sign-in screen.
- [ ] Build the sign-out flow.
- [ ] Design and implement the Firestore data model for to-dos.
- [ ] Write security rules so each user can read and write only their own to-dos.
- [ ] Write a rules test (or a manual two-account test) proving the rule works — confirm it fails
      before the fix and passes after.

## Verify

- [ ] Verify auth works on both platforms.
- [ ] Verify the rules test (or two-account proof) shows user B cannot read user A's data.
- [ ] Do a final self-review against every checkbox in `brief.md`'s Definition of done.

## Write-up

- [ ] Write "What I built" in `write-up-template.md`.
- [ ] Write "Why it's built this way (key decisions)": your Firestore data model and why that
      shape, and how you wrote and proved your security rule — what the failing case looked like
      before the fix.
- [ ] Write "How to build it (teach it to the next trainee)": a guide to wiring Firebase into a
      bare React Native project and locking data down per user, using your own rules as the worked
      example.
- [ ] Write "Concepts worth explaining": pick 1-2 ideas (how Firestore security rules actually
      evaluate, or why config files need native wiring instead of just an npm install) and explain
      each in your own words.
- [ ] Write "What tripped me up": config file placement, Gradle/Xcode wiring surprises, anything
      your first rules attempt got wrong.
- [ ] Write "Checkpoint evidence": auth working on both platforms, and the proof that user B cannot
      read user A's data.
- [ ] Write "What I'd do differently."
- [ ] Author `module_06.md` (teaching material for the content library), once write-up-template.md
      is filled in and your build passes VALIDATE: draw the lesson from write-up-template.md's
      "How to build it," "Concepts worth explaining," and "Why it's built this way" sections (not
      its "What tripped me up" / "What I'd do differently" narrative). Close the file with exactly
      5 open-ended comprehension questions — one per distinct concept (reuse concepts if fewer than
      5 distinct ones exist — never pad with an unrelated question to hit the count), never yes/no,
      never containing the answer — and an Understanding Checklist with one self-assessable item
      per question.
