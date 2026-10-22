# M09 Tasks — Professional UI and Core Components

Build a polished, accessible and fast UI with a component library, and find simple performance
problems before they become real ones.

> There is no solutions file for this stage. This checklist guides the work; it doesn't contain it.

## Setup

- [ ] Read this stage's `brief.md` fully.
- [ ] Research React Native Paper: theming, dark mode, common components.
- [ ] Research FlatList tuning techniques: stable keys, memoized rows, and what causes unnecessary
      re-renders.
- [ ] Research swipe gestures with Gesture Handler, and light animation with Reanimated.
- [ ] Research patterns for loading, empty and error states.
- [ ] Research forms and keyboard handling in this context.
- [ ] Research how to use the React DevTools profiler to find re-renders.
- [ ] Re-read your M04 accessibility checklist before you start, since you'll re-run it here.

## Build

- [ ] Apply a React Native Paper theme, including dark mode.
- [ ] Add swipe-to-delete with Gesture Handler.
- [ ] Build loading, empty and error states for the to-do list.
- [ ] Seed the list with 2,000 to-dos for testing, and profile it with the React DevTools profiler.
- [ ] Tune the FlatList based on what the profiler shows: stable keys, memoized rows, and whatever
      else is re-rendering unnecessarily.
- [ ] Build a release build and confirm the scroll is smooth with 2,000 to-dos — not in debug.
- [ ] Re-run the M04 accessibility checklist against the updated screens, including a screen reader
      pass on both platforms.

## Verify

- [ ] Verify 2,000 to-dos scroll smoothly in a release build.
- [ ] Verify the accessibility checklist passes.
- [ ] Do a final self-review against every checkbox in `brief.md`'s Definition of done.

## Write-up

- [ ] Write "What I built" in `write-up-template.md`.
- [ ] Write "Why it's built this way (key decisions)": what the profiler actually showed was
      re-rendering and what you changed to fix it, and what's different about the list in release
      vs. debug and why that mattered for the 2,000-item test.
- [ ] Write "How to build it (teach it to the next trainee)": a guide to tuning a FlatList for a
      long, frequently-updated list, using your own before/after profiler results as the worked
      example.
- [ ] Write "Concepts worth explaining": pick 1-2 ideas (why debug and release builds perform
      differently, or what actually makes a FlatList row re-render) and explain each in your own
      words.
- [ ] Write "What tripped me up": performance surprises, gesture/animation conflicts, anything the
      accessibility re-pass caught that the first pass in M04 missed.
- [ ] Write "Checkpoint evidence": the 2,000-item scroll performance in a release build, and the
      accessibility checklist passing.
- [ ] Write "What I'd do differently."
- [ ] Author `module_09.md` (teaching material for the content library), once write-up-template.md
      is filled in and your build passes VALIDATE: draw the lesson from write-up-template.md's
      "How to build it," "Concepts worth explaining," and "Why it's built this way" sections (not
      its "What tripped me up" / "What I'd do differently" narrative). Close the file with exactly
      5 open-ended comprehension questions — one per distinct concept (reuse concepts if fewer than
      5 distinct ones exist — never pad with an unrelated question to hit the count), never yes/no,
      never containing the answer — and an Understanding Checklist with one self-assessable item
      per question.
