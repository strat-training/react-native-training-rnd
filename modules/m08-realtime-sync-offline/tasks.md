# M08 Tasks — Real-Time Sync and Offline

Keep two devices in sync in real time, and make the app genuinely useful with no network at all.

> There is no solutions file for this stage. This checklist guides the work; it doesn't contain it.

## Setup

- [ ] Read this stage's `brief.md` fully.
- [ ] Research Firestore snapshot listeners and how to clean them up correctly.
- [ ] Research Firestore offline persistence and how pending writes behave.
- [ ] Research `@react-native-community/netinfo` and how to surface connection state in the app.
- [ ] Research simple conflict-resolution rules and when last-write-wins genuinely isn't good
      enough.
- [ ] Research how to test sync across two devices (or two simulators/emulators standing in).

## Build

- [ ] Wire Firestore snapshot listeners into the to-do list so changes on one device show up live
      on another.
- [ ] Turn on Firestore offline persistence and confirm pending writes behave the way you expect.
- [ ] Add NetInfo so the app knows and can show its own connection state.
- [ ] Write an airplane-mode test script, or get one from your trainer if this cohort provides it.
- [ ] Run the airplane-mode test across two devices (or two simulators/emulators) and fix whatever
      the first run exposes.

## Verify

- [ ] Verify the airplane-mode test script passes.
- [ ] Verify both devices end with the same data after the network returns.
- [ ] Do a final self-review against every checkbox in `brief.md`'s Definition of done.

## Write-up

- [ ] Write "What I built" in `write-up-template.md`.
- [ ] Write "Why it's built this way (key decisions)": where exactly you set up and tear down your
      snapshot listeners and why there, and what happens when two edits to the same to-do collide —
      is last-write-wins good enough here, and how do you know.
- [ ] Write "How to build it (teach it to the next trainee)": a guide to building a list screen that
      stays correct offline and resyncs cleanly, using the airplane-mode test as the worked example.
- [ ] Write "Concepts worth explaining": pick 1-2 ideas (Firestore's offline persistence model, or
      the difference between a pending write and a synced one) and explain each in your own words.
- [ ] Write "What tripped me up": listener cleanup bugs, conflicting-write surprises, anything the
      two-device test caught that a single-device test wouldn't have.
- [ ] Write "Checkpoint evidence": the airplane-mode test script passing, with both devices ending
      in the same state.
- [ ] Write "What I'd do differently."
- [ ] Author `module_08.md` (teaching material for the content library), once write-up-template.md
      is filled in and your build passes VALIDATE: draw the lesson from write-up-template.md's
      "How to build it," "Concepts worth explaining," and "Why it's built this way" sections (not
      its "What tripped me up" / "What I'd do differently" narrative). Close the file with exactly
      5 open-ended comprehension questions — one per distinct concept (reuse concepts if fewer than
      5 distinct ones exist — never pad with an unrelated question to hit the count), never yes/no,
      never containing the answer — and an Understanding Checklist with one self-assessable item
      per question.
