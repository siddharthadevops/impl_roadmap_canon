# Review/Seal Convergence Formula

Status: closed

## Boundary

Amend the common process so normal reviews converge through Codex CLI first,
Claude CLI second, full official verification brackets review, and seal
findings repeat the full seal round without returning to normal review unless a
fix materially changes scope or design.

## Trial Process

This milestone follows the operator-approved trial formula for implementation,
review, seal, and closure. The skeleton and slice note are intentionally thin
local state for that trial; the implementation review covers the milestone
state and canon wording together.

## Non-Goals

- Do not add automation or new runner scripts.
- Do not weaken worktree snapshots, no-edit review prompts, egress rules, or
  seal independence.
- Do not keep sub-agent reviewers in the common canon.
- Do not add product-specific verification commands.

## Canonical Basis

- Common process: [`../../../canon/process/README.md`](../../../canon/process/README.md)
- Review runner: [`../../../canon/process/codex-review.md`](../../../canon/process/codex-review.md)
- Local context: [`../../local-context.md`](../../local-context.md)
- Prior reviewed release: `v0.5.0`
- Operator direction: implement the new convergence formula with CLI-only Codex
  and Claude reviews, seals, and disagreement dialogues.

## Reuse Posture

- Checked: current review loop, double-seal rules, consultation/adjudication
  rules, review runner invocations, local context, and prior S4 release state.
- Reused or extended: existing CLI runner evidence, worktree snapshots,
  no-peek double seal, local verification commands, finding triage, and
  operator escalation.
- New machinery, if any: no tooling; only convergence-order process language.
- Compatibility: consumers keep their local verification commands and review
  evidence layout while running both normal review families before sealing.
- Local context: this product-neutral canon repo records no support order and
  no sensitive local exclusions.

## Shared Contract

Reviews and seals are CLI-run, review-only evidence. Normal review must become
clean in Codex CLI and then Claude CLI before sealing. A valid seal finding
loops back to another full seal round, not to normal reviews, unless the fix
substantially changes scope or design.

## Slices

| Slice | Title | Status | Notes |
|---|---|---|---|
| 01 | Review/seal convergence formula | closed | Reviewed release `v0.6.0`; no accepted debt. |

## Work Log

| Unit | Phase | Status | Review | Commit | Notes |
|---|---|---|---|---|---|
| Skeleton | doc | ready | operator-approved trial | | Thin local state for S5. |
| Slice 01 | doc | ready | operator-approved trial | | Slice note drafted for the approved canon change. |
| Slice 01 | impl | review_clean | slice-01-impl-r3 + seal-a1 | ebc5059 | Codex and Claude normal reviews clean; double seal clean. |
| Slice 01 | closure | closed | | | Closure/bookkeeping recorded. |

## Current Slice

None. S5 is closed.

## Continuation

S5 is closed. Continue by reading the global milestone index and roadmap before
opening any future canon change.
