# M10 — Push Notifications with FCM

**Week 2 · Day 5 · 4 hours**

## Builds on

[M09](../m09-professional-ui-core-components/write-up-template.md) — the polished, synced to-do app
is what now receives and reacts to a real push notification.

## Objective

Deliver push notifications through Firebase Cloud Messaging, with no hosted push service from Expo.

## Scope

- `@react-native-firebase/messaging`.
- Permissions: the iOS prompt and the Android 13+ notification permission.
- APNs key setup inside Firebase, device tokens, Android notification channels.
- Foreground, background and quit app states, and how delivery differs across them.
- Opening a specific screen when the user taps a notification.
- Sending a push from a local Node script using the Firebase Admin SDK — this course does not use
  Cloud Functions, which need a paid Firebase plan.

## Stack constraints

- Same pins as M01–M09. `@react-native-firebase/messaging`, pinned in your lockfile.

## Resolved: push comes from a local script, not Cloud Functions

This program always sends push from a local Node script with the Firebase Admin SDK, never from
Cloud Functions. The Expo push service is also out of scope — it would add a hosted dependency this
course deliberately avoids.

## Deliverable

**A push notification sent when a to-do is shared or assigned, opening that item on tap, tested on
a real iPhone and a real Android device across foreground, background and quit states.**

## Lab

*Goal: deliver a real push end to end, including the state transitions and the permission-denied
path that are easy to skip in a demo.*

**You do.**

1. Set up the APNs key in Firebase and confirm device tokens register on both platforms.
2. Handle the iOS permission prompt and the Android 13+ notification permission, including the
   denied path.
3. Set up Android notification channels.
4. Write the local Node script (Firebase Admin SDK) that sends a push when a to-do is shared or
   assigned.
5. Handle the notification in foreground, background and quit states, and open the relevant to-do
   on tap.
6. Test the full flow on a real iPhone and a real Android device.

**You build and capture.** The push working end to end on real devices across all three app states,
and the denied-permission path handled without a crash.

## Definition of done

- [ ] Push works on a real iPhone and a real Android device.
- [ ] The denied-permission path does not crash.

## Logistics

- Confirm Apple account access with your trainer before this module — creating the APNs push key
  needs a paid Apple Developer account, and this needs to be settled before Week 2, not only before
  the capstone's deploy workshop.
