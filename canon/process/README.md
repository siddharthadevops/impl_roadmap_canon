# Development Process Canon

Status: common canon

This is the shared delivery process for implementation roadmaps. It is AI-led,
review-driven, and slice-by-slice. A consuming project pins this repository and
keeps live project state in its own `implementation/` tree.

## Authority Split

The canon owns process invariants:

- `milestone -> slice` hierarchy.
- one active slice at a time.
- documentation before implementation.
- review rounds and double final seals.
- durable review logs and closure records.
- continuation from recorded local state, not chat memory.

The consuming project owns local state:

- strategic roadmap.
- milestone registry and active continuation.
- milestone work logs.
- `review-log.md` files.
- `closures/`.
- accepted debt and local mandates.

## Required Local Layout

```text
implementation/
  README.md
  roadmap.md
  process/
    README.md          # local pointer to this canon, plus temporary deviations if any
    codex-review.md    # local pointer to this canon, plus temporary deviations if any
    review-log.md      # only for process-doc reviews
  milestones/
    README.md          # global local registry and active continuation
    <milestone>/
      README.md        # skeleton, work log, current slice, continuation rule
      review-log.md
      slices/
      closures/
  review-work/         # git-ignored scratch evidence
```

## Hierarchy

- `milestone`: a meaningful functional outcome.
- `slice`: the smallest reviewable, approvable, and closeable delivery unit.

There is no block level. Keep slices narrow: one clear intent, one reviewable
surface, no unrelated scope.

## Reuse Gate

Before a skeleton, slice note, or implementation proposes new machinery, it must
first check existing project code, existing project contracts, pinned shared
dependencies, and already-approved platform surfaces. Prefer reuse, extension,
wrapping, parameterization, or documentation over parallel machinery.

Every skeleton and slice note must include a short `Reuse Posture` section:

- what was checked.
- what is reused or extended.
- why any new machinery is necessary.
- how the new path stays compatible with existing contracts.

## Cycle

1. **Milestone skeleton.** Create the milestone `README.md`, `slices/`,
   `closures/`, and `review-log.md`. Review the skeleton until sealed `ready`.
   Commit the sealed skeleton before slice work begins.
2. **Slice documentation.** Draft the slice note: scope, non-goals, expected
   files, dependencies, acceptance criteria, tests, risks, and reuse posture.
   Review until sealed `ready`. Commit the sealed slice note before production
   code begins.
3. **Slice implementation.** Implement only the approved scope. Verify, commit
   the implementation, review until sealed `review_clean`, write the closure,
   update logs, then commit bookkeeping separately.

Work one slice to closure before opening the next. A blocked slice remains the
current slice until it is resolved or explicitly deferred in local state.

## Reviews

Reviews are run by the orchestrator, not supplied by the operator. Use
[`codex-review.md`](codex-review.md) for the common evidence contract.

Each phase has:

- iterative Codex review rounds.
- triage for every finding: fixed, rejected with rationale, or operator-accepted
  debt.
- a double final seal on an unchanged artifact.

`P0` and `P1` findings cannot become debt. `P2` and `P3` debt requires explicit
operator acceptance and must be recorded in local state.

## Reopen Rule

A seal covers an unchanged artifact. A later substantive change to sealed
documentation reopens documentation review. A later substantive change to
sealed implementation reopens implementation review.

Bookkeeping updates do not reopen a phase unless they alter reviewed process
rules or artifact substance.

## End-To-End Mandates

A project may record an end-to-end mandate in local state. The mandate allows
the orchestrator to continue through normal gates without pausing for operator
approval between sealed units.

The mandate does not weaken gates. Skeletons still seal before slice notes,
slice notes still seal before implementation, implementation still verifies
before review, and closures still record the sealed outcome.

Push mandates are local state. Never push unsealed work, unresolved review
states, unrelated local changes, or commits outside the recorded mandate.

## Documentation Discipline

Documentation artifacts are contracts for implementation and review. Keep them
short and executable:

- boundary.
- canonical basis.
- reuse posture.
- scope and non-goals.
- acceptance criteria.
- tests and risks.
- current continuation state.

Avoid pseudo-code, defensive FAQs, repetition, and future milestone chains. If a
document starts specifying control flow that belongs in code, reduce it to
observable contracts, invariants, and tests.

