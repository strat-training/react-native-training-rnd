# M10 Tasks — Push Notifications with FCM

Deliver push notifications through Firebase Cloud Messaging, with no hosted push service from Expo.

> There is no solutions file for this stage. This checklist guides the work; it doesn't contain it.

## Setup

- [ ] Read this stage's `brief.md` fully, including the Logistics section.
- [ ] Confirm with your trainer: Apple account access for the APNs push key, before starting this
      module.
- [ ] Research `@react-native-firebase/messaging`.
- [ ] Research the iOS permission prompt and the Android 13+ notification permission, including the
      denied path.
- [ ] Research APNs key setup inside Firebase, device tokens, and Android notification channels.
- [ ] Research how notification delivery differs across foreground, background and quit app states.
- [ ] Research how to open a specific screen when the user taps a notification.
- [ ] Research sending push from a local Node script with the Firebase Admin SDK, and why this
      course avoids Cloud Functions and the Expo push service.

## Build

- [ ] Set up the APNs key in Firebase and confirm device tokens register on both platforms.
- [ ] Handle the iOS permission prompt and the Android 13+ notification permission, including the
      denied path.
- [ ] Set up Android notification channels.
- [ ] Write the local Node script (Firebase Admin SDK) that sends a push when a to-do is shared or
      assigned.
- [ ] Handle the notification in foreground, background and quit states, and open the relevant
      to-do on tap.
- [ ] Test the full flow on a real iPhone and a real Android device.

## Verify

- [ ] Verify push works on a real iPhone and a real Android device.
- [ ] Verify the denied-permission path does not crash.
- [ ] Do a final self-review against every checkbox in `brief.md`'s Definition of done.

## Write-up

- [ ] Write "What I built" in `write-up-template.md`.
- [ ] Write "Why it's built this way (key decisions)": how your local Node script decides when to
      send a push and what its payload looks like, and how you handled the three app states
      differently, if at all.
- [ ] Write "How to build it (teach it to the next trainee)": a guide to delivering a push
      notification end to end on both platforms, using your own sending script and tap-handling
      code as the worked example.
- [ ] Write "Concepts worth explaining": pick 1-2 ideas (why Cloud Functions need a paid plan and
      what a local Admin SDK script replaces, or why Android 13+ needs an explicit runtime
      permission for notifications) and explain each in your own words.
- [ ] Write "What tripped me up": APNs key setup, token registration surprises, permission-denied
      edge cases, anything that only showed up on a real device.
- [ ] Write "Checkpoint evidence": push working on a real iPhone and a real Android device, and the
      denied-permission path not crashing.
- [ ] Write "What I'd do differently."
- [ ] Author `module_10.md` (teaching material for the content library), once write-up-template.md
      is filled in and your build passes VALIDATE: draw the lesson from write-up-template.md's
      "How to build it," "Concepts worth explaining," and "Why it's built this way" sections (not
      its "What tripped me up" / "What I'd do differently" narrative). Close the file with exactly
      5 open-ended comprehension questions — one per distinct concept (reuse concepts if fewer than
      5 distinct ones exist — never pad with an unrelated question to hit the count), never yes/no,
      never containing the answer — and an Understanding Checklist with one self-assessable item
      per question.
