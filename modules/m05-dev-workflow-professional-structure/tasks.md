# M05 Tasks — Dev Workflow and Professional Structure

Choose the right debug and build loop for a given change, and organize the project so a team could
actually work in it.

> There is no solutions file for this stage. This checklist guides the work; it doesn't contain it.

## Setup

- [ ] Read this stage's `brief.md` fully.
- [ ] Research development builds vs. Expo Go, and why Expo Go can't load the native modules you've
      already linked.
- [ ] Research Fast Refresh and how to recognize when a change needs a native rebuild instead.
- [ ] Research React Native DevTools (the Flipper replacement) and its network inspector.
- [ ] Research the standard project structure (`components`, `navigation`, `services`, `utils`,
      `assets`) and what belongs in each.
- [ ] Research how to wrap a raw storage API behind a clean service interface.
- [ ] Research TypeScript, ESLint and Prettier setup conventions for a React Native project.
- [ ] Research migration strategies: what dropping Expo tooling later would take, and what adding
      more Expo packages later would take.

## Build

- [ ] Move the profile app into the standard folder layout (`components`, `navigation`, `services`,
      `utils`, `assets`).
- [ ] Build the storage service wrapping AsyncStorage, and route all persistence through it.
- [ ] Replace every direct AsyncStorage call in screens with calls through the storage service.
- [ ] Set up (or confirm and tighten) TypeScript, ESLint and Prettier.
- [ ] Re-run the app on both platforms after the move and confirm nothing broke.
- [ ] Optional, not scheduled/not graded: rebuild the same app with `react-native init`, copy your
      `src/` folder across unchanged, and compare the two setups.

## Verify

- [ ] Verify TypeScript and lint both pass.
- [ ] Verify the app still runs on both platforms after the folder move.
- [ ] Verify all persistence goes through the storage service, not directly through AsyncStorage.
- [ ] Do a final self-review against every checkbox in `brief.md`'s Definition of done.

## Write-up

- [ ] Write "What I built" in `write-up-template.md`.
- [ ] Write "Why it's built this way (key decisions)": your storage service's actual interface and
      why you shaped it that way, and the folder structure you landed on and what you'd put
      elsewhere next time.
- [ ] Write "How to build it (teach it to the next trainee)": a guide to wrapping AsyncStorage
      behind a clean service interface, using your own service as the worked example.
- [ ] Write "Concepts worth explaining": pick 1-2 ideas (Fast Refresh vs. a native rebuild, or why
      Expo Go couldn't run your app anymore once you linked native modules) and explain each in
      your own words.
- [ ] Write "What tripped me up": restructure breakage, lint/TypeScript friction, DevTools
      surprises.
- [ ] Write "Checkpoint evidence": TypeScript and lint passing, and the app running on both
      platforms after the move.
- [ ] Write "What I'd do differently" (including what the take-home `react-native init` comparison
      taught you, if you did it).
- [ ] Author `module_05.md` (teaching material for the content library), once write-up-template.md
      is filled in and your build passes VALIDATE: draw the lesson from write-up-template.md's
      "How to build it," "Concepts worth explaining," and "Why it's built this way" sections (not
      its "What tripped me up" / "What I'd do differently" narrative). Close the file with exactly
      5 open-ended comprehension questions — one per distinct concept (reuse concepts if fewer than
      5 distinct ones exist — never pad with an unrelated question to hit the count), never yes/no,
      never containing the answer — and an Understanding Checklist with one self-assessable item
      per question.
