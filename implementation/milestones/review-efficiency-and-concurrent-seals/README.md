# Review Efficiency And Concurrent Seals

Status: open (Slice 01 documentation)

## Boundary

Amend the common review canon so reviews prefer the local checkout for content
inspection and double final seals launch independent reviewers concurrently
when possible.

## Non-Goals

- Do not weaken no-edit, worktree invalidation, egress, or usable-output rules.
- Do not remove Git from review evidence; Git remains the way to identify and
  compare the reviewed change.
- Do not require prompts to enumerate every local search command.
- Do not change the mandatory Codex plus Claude CLI double-seal pairing.

## Canonical Basis

- Common process: [`../../../canon/process/README.md`](../../../canon/process/README.md)
- Review runner: [`../../../canon/process/codex-review.md`](../../../canon/process/codex-review.md)
- Local context: [`../../local-context.md`](../../local-context.md)
- Prior reviewed release: `v0.3.0`
- Operator direction: review prompts should tell reviewers that the local
  checkout is the source for reading content, while Git is used to identify and
  compare the reviewed change; double-seal halves should run concurrently when
  possible.

## Reuse Posture

- Checked: current `Prompt Shape`, `Worktree Check`, `Watchdog`, and `Seal
  Independence` sections.
- Reused or extended: broad review access, no-edit prompts, worktree snapshots,
  local-context exclusions, and independent double seals.
- New machinery, if any: no tooling; only prompt-shape and seal-ordering
  contract language.
- Compatibility: existing consumers can keep their review runners; the new
  rule changes prompt content and preferred seal scheduling, not artifacts.
- Local context: this canon repo is product-neutral, has no support-order
  constraint, and records no sensitive local exclusions; S3 must keep the common
  rule product-neutral and avoid product-specific review commands.

## Shared Contract

Review prompts should make local inspection explicit: read content from the
checked-out filesystem, use local search and file-reading tools for speed, and
use Git to identify the reviewed scope, compare changes, inspect history, and
verify refs or commits.

Double final seals remain independent and no-peek. When both seal reviewers are
available, launch them concurrently from the same prompt and same unchanged
artifact. If concurrency is not possible, record the reason; sequential launch
does not permit either reviewer to see the other's output before both complete.

These two rules are one reviewable intent: reduce review latency while keeping
the same evidence, no-edit, and independence guarantees.

## Slices

| Slice | Title | Status | Notes |
|---|---|---|---|
| 01 | Review latency reduction without weaker evidence | planned | Add local-checkout prompt guidance and concurrent double-seal rule; publish reviewed tag `v0.4.0`. |

## Work Log

| Unit | Phase | Status | Review | Commit | Notes |
|---|---|---|---|---|---|
| Skeleton | doc | fixed | skeleton-doc-r1 | | Added local-context application to Reuse Posture. |
| Skeleton | doc | fixed | skeleton-doc-r2 | | Added the required commit gate before Slice 01 begins. |
| Skeleton | doc | review_requested | skeleton-doc-r3 + seal-a1 | | Codex r3 clean; seal-a1 found two valid issues. |
| Skeleton | doc | fixed | skeleton-doc-seal-a1 | | Added review-log traceability and one-intent scope justification. |
| Skeleton | doc | fixed | skeleton-doc-r4 | | Updated work-log traceability after r4 finding. |
| Skeleton | doc | fixed | skeleton-doc-r5 | | Updated work-log traceability after r5 finding. |
| Skeleton | doc | fixed | skeleton-doc-r6 | | Updated work-log traceability after r6 finding. |
| Skeleton | doc | fixed | skeleton-doc-r7 | | Updated work-log traceability after r7 finding. |
| Skeleton | doc | fixed | skeleton-doc-r8 | | Updated work-log traceability after r8 finding. |
| Skeleton | doc | fixed | skeleton-doc-r9 | | Updated work-log traceability after r9 finding. |
| Skeleton | doc | review_requested | skeleton-doc-r10 + seal-a2 | | Codex r10 clean; documentation double seal launched. |
| Skeleton | doc | ready | skeleton-doc-r10 + seal-a2 | | Double seal clean; no accepted debt. |

## Current Slice

Slice 01 documentation.

## Continuation

Draft Slice 01, then review and seal it before changing common canon files.
