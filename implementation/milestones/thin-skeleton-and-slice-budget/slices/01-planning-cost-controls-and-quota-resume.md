# Slice 01 - Planning Cost Controls And Quota Resume

Status: ready

## Scope

- Add a thin-skeleton rule: skeletons name planned slices, rough slice intent,
  and shared contracts, but leave slice scope, files, tests, risks, and
  acceptance detail to slice notes.
- Require slice notes to be drafted only after the skeleton is sealed and
  committed.
- Add a slice-size target: aim for under about 500 expected changed lines where
  practical, excluding generated, lockfile, and mechanical changes; justify
  cohesive exceptions.
- Keep durable review logs compact; full prompts and reviewer output stay in
  `review-work`.
- Add a CLI quota/rate-limit rule: when the CLI gives a resume time, record it,
  wait until then, and continue the milestone instead of treating it as blocked.

## Non-Goals

- Do not add tooling, counters, or hard enforcement.
- Do not split cohesive implementation only to satisfy the line target.
- Do not change double-seal pairing, no-edit rules, or worktree snapshots.
- Do not add product-specific verification commands.

## Reuse Posture

- Checked: common process, review runner, milestone template, slice template,
  S3 local-inspection wording, and S4 sealed skeleton.
- Reused or extended: existing milestone/slice sequence, review-work scratch
  boundary, durable review-log model, and CLI runner evidence contract.
- New machinery, if any: none; only canon wording and template defaults.
- Compatibility: consumers keep the same layout and gates.
- Local context: this canon repo has no product stack or support-order
  constraint; wording remains product-neutral.

## Non-Canonical Planning

- Named planning material: operator direction in the active thread.
- Adopt / Revise / Reject: adopt the simple under-about-500-lines target and
  quota-resume rule; revise skeleton/slice wording to avoid hard caps and
  artificial splits; reject adding more numeric thresholds.
- Notes: no external brainstorming artifact is needed.

## Dependencies

- S4 skeleton sealed and committed at `d6b3fd0`.
- Codex CLI and Claude CLI are available for required reviews and seals.

## Expected Files

- `canon/process/README.md`
- `canon/process/codex-review.md`
- `templates/local-state/implementation/milestones/_milestone/README.md`
- `templates/local-state/implementation/milestones/_milestone/slices/01-slice.md`
- `implementation/milestones/thin-skeleton-and-slice-budget/README.md`
- `implementation/milestones/thin-skeleton-and-slice-budget/review-log.md`

## Acceptance Criteria

- Skeleton rules explicitly forbid slice-note drafting before skeleton `ready`
  plus commit.
- Skeleton slice tables use `planned` for unopened slices.
- Slice notes carry the about-500 expected changed-line target and cohesive
  exception rationale.
- Durable review logs are described as summaries, not full review transcripts.
- CLI quota/rate-limit errors with provider resume times are treated as a wait
  and resume condition, not milestone blockage.
- The change remains product-neutral and does not add tooling.

## Tests

- `rg -n "Skeletons.*planned slices|slice notes.*after the skeleton" canon/process/README.md`
- `rg -n "scope, files, tests, risks" canon/process/README.md`
- `rg -n "planned" templates/local-state/implementation/milestones/_milestone/README.md`
- `rg -n "500|changed lines" canon/process/README.md templates/local-state/implementation/milestones/_milestone/slices/01-slice.md`
- `rg -n "quota|rate-limit|resume" canon/process/codex-review.md`
- `rg -n "review logs.*summar" canon/process/README.md canon/process/codex-review.md`
- `git diff --check`

## Risks

- The line target could be misread as a hard cap. Mitigation: state it as an
  aim and allow cohesive exceptions.
- Skeletons could become too vague. Mitigation: keep shared contracts and rough
  slice intent in skeletons.
- Quota pauses could hide real failures. Mitigation: only resume automatically
  when the CLI gives a concrete resume time.

## Review

This slice note must seal `ready` and be committed before canon or template
changes begin.
