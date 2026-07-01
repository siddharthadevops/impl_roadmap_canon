# Thin Skeleton And Slice Budget Discipline

Status: Slice 01 documentation sealed; implementation pending

## Boundary

Amend the common process so milestone skeletons stay thin, slice notes are
drafted just in time, slices target small reviewable diffs, durable review logs
stay compact, and CLI quota pauses resume from the recorded continuation state.

## Non-Goals

- Do not add automation or hard line-count enforcement.
- Do not weaken review, double-seal, no-edit, or worktree evidence rules.
- Do not force artificial splits when one cohesive change is safer.
- Do not define product-specific slice sizes or local verification commands.

## Canonical Basis

- Common process: [`../../../canon/process/README.md`](../../../canon/process/README.md)
- Review runner: [`../../../canon/process/codex-review.md`](../../../canon/process/codex-review.md)
- Local context: [`../../local-context.md`](../../local-context.md)
- Local templates: [`../../../templates/local-state/implementation/milestones/_milestone/README.md`](../../../templates/local-state/implementation/milestones/_milestone/README.md)
- Prior reviewed release: `v0.4.0`
- Operator direction: keep skeletons thin, draft slice notes only after the
  skeleton seals, aim slices below about 500 expected changed lines where
  practical, keep durable review logs compact, and resume CLI quota pauses at
  the provider-stated time.

## Reuse Posture

- Checked: current hierarchy, cycle, documentation discipline, review output,
  template skeleton, slice template, and S3 review runner language.
- Reused or extended: existing milestone/slice gates, current one-slice-at-a-time
  process, `review-work` scratch boundary, and CLI runner evidence model.
- New machinery, if any: no new tooling; only sharper process language and
  template defaults.
- Compatibility: consumers keep the same layout and review commands; the new
  rules reduce premature artifact size and clarify quota retry behavior.
- Local context: this canon repo has no product stack or support-order
  constraint; S4 remains product-neutral.

## Shared Contract

Skeletons authorize planning, not slice execution. They name planned slices and
their rough intent, but leave slice scope, files, tests, risks, and acceptance
detail to the slice note drafted after the skeleton is sealed and committed.

Durable review logs summarize review state, findings, triage, seal outcomes, and
debt. Long prompts and full reviewer output stay in git-ignored `review-work/`.

These rules are one reviewable intent: keep planning and review loops
manageable under real review cost, including oversized artifacts and temporary
CLI quota pauses.

## Slices

| Slice | Title | Status | Notes |
|---|---|---|---|
| 01 | Planning cost controls and quota resume rule | doc ready | Add thin-skeleton, just-in-time slice-note, slice budget, compact review-log, and CLI quota-resume rules. |

## Work Log

| Unit | Phase | Status | Review | Commit | Notes |
|---|---|---|---|---|---|
| Skeleton | doc | ready | skeleton-doc-r3 + seal-a3 | | Double seal clean; no accepted debt. |
| Slice 01 | doc | ready | slice-01-doc-r4 + seal-a3 | | Double seal clean; no accepted debt. |

## Current Slice

Slice 01 implementation.

## Continuation

Commit the sealed Slice 01 note, then implement only the approved canon and
template changes.
