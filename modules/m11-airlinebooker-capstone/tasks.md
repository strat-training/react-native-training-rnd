# M11 Tasks — AirlineBooker Pro (Team Capstone)

Work as a team on one codebase through pull requests and code review, design a clean app structure
and hold it under time pressure, and ship signed release candidates for both platforms.

> There is no solutions file for this stage. This checklist guides the work; it doesn't contain it.

## Setup

- [ ] Read this stage's `brief.md` fully, including the Logistics section.
- [ ] Confirm with your program owner, before Week 1: the store-account model for this cohort
      (instructor-owned vs. your own).
- [ ] Confirm with your trainer, before Day 6: the fallback release gate if your cohort has no
      store accounts (default: a signed build installed and running on a device, without the store
      tracks).
- [ ] Confirm with your trainer: your team's Mac and real-device pool.
- [ ] If your program owner has swapped in a different capstone brief, get its scope-tier list
      before you start.
- [ ] Confirm with your trainer, before Day 1: your team's size and which scope floor applies (solo
      = must-have only, 2-3 = should-have expected, 4-5 = could-have expected).
- [ ] As a team, re-read your own M03, M06, M07-M08, M09 and M10 write-ups before Day 1 — there is
      no reference solution for this stage.
- [ ] Research the end-to-end tool for this capstone: Maestro by default, or whatever your trainer
      names instead.
- [ ] Research a maps library for the should-have map feature, in case your team takes it on.

## Build

- [ ] Day 1: run Workshop A, write your architecture decisions down as short ADRs, and agree on
      folder layout and import rules.
- [ ] Day 1: stand up the repo, CI (lint, type-check, tests), Dev/Staging/Prod variants, your team's
      Firebase projects per environment, and seed flight data.
- [ ] Day 1: agree as a team who owns billing alerts for your Firebase projects, and how your
      Firebase Admin key is distributed and kept out of Git.
- [ ] Day 1: split the must-have work into vertical slices sized to your team, and assign the first
      two-day role rotation across whatever roles your team size supports (a solo capstone rotates
      focus across all five instead of rotating people between them).
- [ ] Days 2-4: build sign-up, sign-in and the secure session, with an auth-guarded navigation flow.
- [ ] Days 2-4: build flight search with filters (from, to, date, passengers) and a results list.
- [ ] Days 2-4: build flight detail, the passenger form, booking saved to Firestore, and the My
      Bookings screen.
- [ ] Day 5: integrate the team's work and run the mid-point demo.
- [ ] Day 5: run Workshop B, and get unit/component tests plus CI (lint, type-check, tests) running
      on GitHub Actions.
- [ ] Day 6: run Workshop D part 1, and get a signed skeleton build into TestFlight and the Play
      internal track (or the confirmed fallback gate).
- [ ] Day 6: pick up a should-have (payments in Stripe test mode, or seat selection) if there's
      time.
- [ ] Day 7: design and build your team's push-sending Node service (architecture is yours to work
      out), and wire the booking-confirmation push to open the booking.
- [ ] Day 7: build offline support so My Bookings also opens with no network.
- [ ] Day 8: pick up maps or a could-have feature, and run an accessibility and performance pass if
      there's time.
- [ ] Day 8: run Workshop C, profile the app in a release build, and wire up crash reporting.
- [ ] Day 9: run Workshop D part 2 and finish the release build pipeline.
- [ ] Day 9: finish the one end-to-end flow (login, search, book), and harden the release branch.
- [ ] Day 10: finalize signed builds for both platforms, deliver the 10-minute demo plus Q&A, and run
      your team retro.

## Verify

- [ ] Verify every must-have feature works.
- [ ] Verify a tester installs both signed builds from the store tracks (or the confirmed fallback
      gate).
- [ ] Verify the team delivered a 10-minute demo plus Q&A.
- [ ] Score yourselves against the 100-point rubric, with evidence for each row, and confirm the
      total is 70 or more.
- [ ] Do a final self-review against every checkbox in `brief.md`'s Definition of done.

## Write-up

- [ ] Write "What we built" in `write-up-template.md`.
- [ ] Write "Why it's built this way (key decisions)": your Workshop A architecture decisions and
      whether they held up under the deadline, your push-sending service's (and payment stub's, if
      built) design and what you'd change, and how work was split into vertical slices and how the
      five rotating roles actually played out.
- [ ] Write "How to build it (teach it to the next trainee)": a guide to one meaningfully hard piece
      of this capstone — the booking flow's Firestore transaction, the offline + push interaction,
      or your release pipeline — using your own implementation as the worked example.
- [ ] Write "Concepts worth explaining": pick 2-3 ideas from across the whole program that this
      capstone forced you to actually understand, not just use.
- [ ] Write "What tripped me up": team-process friction, integration surprises, anything about
      running your own Firebase/push infrastructure that cost more time than expected.
- [ ] Write "Checkpoint evidence": every must-have feature working, both signed builds installed by
      a tester, and your rubric self-score with evidence for each row.
- [ ] Write "What we'd do differently": in the architecture, the schedule, or how the team worked
      together.
- [ ] Author `module_11.md` (teaching material for the content library), once write-up-template.md
      is filled in and your build passes VALIDATE: draw the lesson from write-up-template.md's
      "How to build it," "Concepts worth explaining," and "Why it's built this way" sections (not
      its "What tripped me up" / "What we'd do differently" narrative). Close the file with exactly
      5 open-ended comprehension questions — one per distinct concept (reuse concepts if fewer than
      5 distinct ones exist — never pad with an unrelated question to hit the count), never yes/no,
      never containing the answer — and an Understanding Checklist with one self-assessable item
      per question.
