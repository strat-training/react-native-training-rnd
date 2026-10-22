# M07 Tasks — State and Server Data

Pick the right place for each kind of state, and make the UI feel instant while data saves in the
background.

> There is no solutions file for this stage. This checklist guides the work; it doesn't contain it.

## Setup

- [ ] Read this stage's `brief.md` fully, including both Resolved sections.
- [ ] Research Zustand: CRUD-style stores, selectors, persistence.
- [ ] Research React Context for app-wide settings like theme and the auth session.
- [ ] Research TanStack Query: caching, retries, mutations, invalidation.
- [ ] Research optimistic updates and rollback patterns.
- [ ] Research error boundaries in React Native.
- [ ] Research how to structure a service layer between screens/stores and Firebase, with Zod
      validation at its edges.
- [ ] Research how to write a lint rule that fails the build if code outside `services/` imports
      Firebase.

## Build

- [ ] Build the to-do Zustand store: create, read, update, delete.
- [ ] Build the service layer between the store and Firestore, with Zod validation at its edges.
- [ ] Add optimistic updates so the UI reflects a change before the network confirms it.
- [ ] Force a save to fail and confirm the optimistic update rolls back and the user sees an error.
- [ ] Add an error boundary somewhere it would actually catch something real.
- [ ] Wire theme and the auth session through Context.
- [ ] Write the lint rule that fails the build if a screen or store imports Firebase directly
      instead of going through the service layer.

## Verify

- [ ] Verify a forced save failure rolls back the optimistic update and shows an error.
- [ ] Verify every piece of state you added this stage lives in one of the three homes (Zustand,
      Context, TanStack Query) — and that you can name which one and why.
- [ ] Verify the lint rule actually fails the build on a deliberate violation, then passes once
      it's removed.
- [ ] Do a final self-review against every checkbox in `brief.md`'s Definition of done.

## Write-up

- [ ] Write "What I built" in `write-up-template.md`.
- [ ] Write "Why it's built this way (key decisions)": how you implemented the optimistic update
      and its rollback specifically, your service layer's interface and where Zod validation sits
      in it, and how you enforced Firebase-behind-services — the actual lint rule.
- [ ] Write "How to build it (teach it to the next trainee)": a guide to building an
      optimistic-update flow with a clean rollback path, using your own to-do store as the worked
      example.
- [ ] Write "Concepts worth explaining": pick 1-2 ideas (the three-way state split, or what actually
      makes an optimistic update safe to roll back) and explain each in your own words.
- [ ] Write "What tripped me up": rollback edge cases, cache invalidation surprises, anything that
      made the lint rule harder than expected.
- [ ] Write "Checkpoint evidence": a forced save failure rolling back the optimistic update and
      surfacing an error.
- [ ] Write "What I'd do differently."
- [ ] Author `module_07.md` (teaching material for the content library), once write-up-template.md
      is filled in and your build passes VALIDATE: draw the lesson from write-up-template.md's
      "How to build it," "Concepts worth explaining," and "Why it's built this way" sections (not
      its "What tripped me up" / "What I'd do differently" narrative). Close the file with exactly
      5 open-ended comprehension questions — one per distinct concept (reuse concepts if fewer than
      5 distinct ones exist — never pad with an unrelated question to hit the count), never yes/no,
      never containing the answer — and an Understanding Checklist with one self-assessable item
      per question.
