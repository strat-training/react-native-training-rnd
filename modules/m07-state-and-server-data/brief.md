# M07 — State and Server Data

**Week 2 · Day 2 · 4 hours**

## Builds on

[M06](../m06-firebase-bare-project/write-up-template.md) — auth and the Firestore data model from
that stage are what the to-do store now reads and writes through.

## Objective

Pick the right place for each kind of state, and make the UI feel instant while data saves in the
background.

## Scope

- Zustand stores: CRUD, selectors, persistence.
- React Context for app-wide settings such as theme and the auth session.
- TanStack Query for server state: caching, retries, mutations, invalidation.
- Optimistic updates and rollback.
- Error boundaries.
- A service layer between screens and Firebase, with typed data (Zod validation at the service
  edges).

## Stack constraints

- Same pins as M01–M06. Zustand and TanStack Query, pinned in your lockfile.

## Resolved: state has three homes

This program always splits state the same way: Zustand for client state, Context for theme and the
auth session, TanStack Query for server data. Don't reach for a fourth place to put state — if
something doesn't fit one of these three, that's a sign to look harder at which one it actually
belongs in.

## Resolved: Firebase stays behind the services

No screen or store imports Firebase directly — only the service layer does. You'll want a lint rule
that fails the build if this is violated; how to write that rule is yours to work out.

## Deliverable

**The to-do store (create, read, update, delete) with optimistic updates, connected to Firestore
through a service layer, with a forced save failure rolling back cleanly and surfacing an error.**

## Lab

*Goal: make state feel instant without lying to the user when a save actually fails.*

**You do.**

1. Build the to-do Zustand store: create, read, update, delete.
2. Build the service layer between the store and Firestore, with Zod validation at its edges.
3. Add optimistic updates so the UI reflects a change before the network confirms it.
4. Force a save to fail (bad network, a rejected write, whatever you can simulate) and confirm the
   optimistic update rolls back and the user sees an error.
5. Add an error boundary somewhere it would actually catch something real.
6. Wire theme and the auth session through Context.

**You build and capture.** The to-do CRUD flow working end to end, and the forced-failure rollback
actually demonstrated, not just asserted.

## Definition of done

- [ ] A forced save failure rolls back the optimistic update and shows an error.
