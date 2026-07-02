# Slice 01 - Review/Seal Convergence Formula

Status: ready

## Scope

- Add the convergence formula to the common process and review runner canon.
- Require normal Codex CLI review rounds to reach clean before normal Claude CLI
  review rounds begin.
- Require the full official verification suite before normal review and again
  after normal reviews.
- Require valid seal findings to repeat the full seal round only unless the fix
  substantially changes scope or design.
- Require Codex/Claude reviews, seals, and disagreement dialogues to use CLI
  invocations.
- Replace sub-agent reviewer references in common canon with CLI-family
  dialogue and operator escalation.
- Publish the reviewed release as `v0.6.0`.

## Non-Goals

- Do not add automation, wrappers, or new scripts.
- Do not change the broad CLI command shapes except where needed to identify
  normal Codex and Claude review families.
- Do not weaken worktree snapshots, no-edit prompts, egress limits, no-peek
  seal independence, or finding triage.
- Do not edit historical milestone records except S5 state.

## Reuse Posture

- Checked: current process README, review runner canon, S4 closed state, local
  context verification commands, and existing root version/pinning files.
- Reused or extended: current double seal, CLI runner evidence, worktree
  snapshots, finding verification, operator escalation, and review-work storage.
- New machinery, if any: none; this is process wording only.
- Compatibility: consumers keep their verification suite in local context and
  their review-work storage; they add Claude CLI as the second normal review
  family before sealing.
- Local context: this canon repo has no product stack, support order, or
  sensitive local exclusions; wording remains product-neutral.

## Non-Canonical Planning

- Named planning material: operator prompt for S5.
- Adopt / Revise / Reject: adopt the listed formula and CLI-only requirement;
  revise the old same-family/sub-agent consultation wording into opposite CLI
  family dialogue; reject adding new runner tooling.
- Notes: no external brainstorming artifact is needed.

## Dependencies

- S4 closed at reviewed tag `v0.5.0`.
- Codex CLI and Claude CLI are required for normal reviews and seals.
- Official local verification suite: `git diff --check`.

## Slice Size

Aim for under about 500 expected changed lines where practical. This slice
should stay under that target because it changes only process docs and S5 local
state.

## Expected Files

- `README.md`
- `VERSION`
- `canon/process/README.md`
- `canon/process/codex-review.md`
- `implementation/roadmap.md`
- `implementation/milestones/README.md`
- `implementation/milestones/review-seal-convergence-formula/README.md`
- `implementation/milestones/review-seal-convergence-formula/review-log.md`
- `implementation/milestones/review-seal-convergence-formula/slices/README.md`
- `implementation/milestones/review-seal-convergence-formula/slices/01-review-seal-convergence-formula.md`
- `implementation/milestones/review-seal-convergence-formula/closures/README.md`
- `implementation/milestones/review-seal-convergence-formula/closures/01-review-seal-convergence-formula.md`

## Acceptance Criteria

- Common process and review runner describe Codex CLI normal review until clean,
  then Claude CLI normal review until clean.
- Full official verification runs before normal review and again after normal
  reviews.
- Seal findings repeat the full seal round only after local verification unless
  the fix materially changes scope or design.
- Codex and Claude reviews, seals, and disagreement dialogues are CLI-run.
- Conceptual disagreement uses one continuous opposite-family CLI dialogue
  session, at most two rounds, then operator escalation if unresolved.
- Common canon no longer names sub-agent reviewers.
- The release state names reviewed version `v0.6.0`.

## Tests

- `git diff --check`
- `test "$(cat VERSION)" = "0.6.0"`
- `rg -n "checkout v0.6.0" README.md`
- `rg -n "Codex CLI review rounds until Codex.*clean|Codex returns \`VERDICT: 0\`" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude CLI review rounds until Claude.*clean|Claude returns \`VERDICT: 0\`" canon/process/README.md canon/process/codex-review.md`
- `rg -n "full official verification suite" canon/process/README.md canon/process/codex-review.md`
- `rg -n "repeat the full seal round only|return to normal review rounds" canon/process/README.md canon/process/codex-review.md`
- `rg -n "CLI invocations|continuous CLI dialogue|opposite LLM family" canon/process/README.md canon/process/codex-review.md`
- `! rg -n "sub-agent|subagent" canon templates`

## Risks

- The new order may be misread as weakening double seal. Mitigation: keep the
  unchanged-artifact, same-prompt, no-peek double seal rules intact.
- Seal fixes could skip meaningful rereview. Mitigation: require normal review
  restart when the fix substantially changes scope or design.
- Dialogue could sprawl. Mitigation: cap it at one continuous session and two
  rounds before operator escalation.

## Review

This slice follows the operator-approved S5 trial formula.
