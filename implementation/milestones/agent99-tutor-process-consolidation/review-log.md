# Review Log

Durable review record for S2.

## Skeleton Documentation

### skeleton-doc-r1

Codex review completed with `VERDICT: 2 findings`, `EXIT=0`.

- `F01 [P1]` fixed: Shared Contract now limits Adopt / Revise / Reject to
  brainstorming and drafts; review scratch is mechanical evidence only.
- `F02 [P1]` fixed: Slice 01 now names local support-order capture and
  enforcement without hard-coding product-specific supports.

### skeleton-doc-r2

Codex review completed with `VERDICT: 2 findings`, `EXIT=0`.

- `F01 [P1]` fixed: broad reviewer invocation is recorded as an
  operator-authorized S2-local deviation until the common rule is amended.
- `F02 [P2]` fixed: Agent99/Tutor review logs are named only as pointers to
  prior failure modes and relevant process text, not authority.

### skeleton-doc-r3

Codex review completed with `VERDICT: 2 findings`, `EXIT=0`.

- `F01 [P1]` fixed: Shared Contract requires reviews and consultations to
  enforce local support-order constraints when new machinery is proposed.
- `F02 [P2]` fixed: Reuse Posture explains why `local-context.md` is needed
  alongside local process/deviation files.

### skeleton-doc-r4

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`.

- `F01 [P1]` fixed: broad reviewer invocation now includes a relevance-driven
  egress boundary for sensitive or unrelated material.

### skeleton-doc-r5

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-r6

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`.

- `F01 [P2]` fixed: the skeleton work-log status now uses
  `review_requested` before the documentation double seal, reserving `ready`
  for the sealed state.

### skeleton-doc-r7

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-seal-a1

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude seal half: `VERDICT: 2 findings`, `EXIT=0`.
- Outcome: seal broken; fixed both findings and returned to the Codex loop.
- `F01 [P2]` fixed: the broad S2 milestone now has three narrow planned
  slices instead of one bundled slice.
- `F02 [P3]` fixed: the skeleton work log now carries an explicit `Order`
  column for deterministic continuation.

### skeleton-doc-r8

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-r9

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-seal-a2

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude seal half: `VERDICT: 3 findings`, `EXIT=0`.
- Outcome: seal broken; fixed all findings and returned to the Codex loop.
- `F01 [P2]` fixed: the durable review log now records `skeleton-doc-r9`,
  and the work log points to that round.
- `F02 [P2]` fixed: release tagging is no longer bundled into the broad
  reviewer invocation slice.
- `F03 [P3]` fixed: the work log uses the same `skeleton-doc-r9` round stem as
  the durable review log and scratch evidence.

### skeleton-doc-r10

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`.

- `F01 [P2]` fixed: Agent99/Tutor canonical references now name only
  `README.md` and `codex-review.md`, excluding review logs as authority.

### skeleton-doc-r11

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`.

- `F01 [P2]` fixed: continuation now returns to documentation review after the
  r10 fix instead of proceeding directly to final seal.

### skeleton-doc-r12

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-r13

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-seal-a3

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude seal half: `VERDICT: 2 findings`, `EXIT=0`.
- Outcome: seal broken; fixed both findings and returned to the Codex loop.
- `F01 [P2]` fixed: Shared Contract now requires safe-by-default review
  invocation and local-context access/egress constraints.
- `F02 [P2]` fixed: Slice 01 now explicitly amends the Required Local Layout
  to include the required local context file.

### skeleton-doc-r14

Codex review completed with `VERDICT: 2 findings`, `EXIT=0`.

- `F01 [P1]` fixed: continuation now returns to documentation review after the
  seal-a3 fixes instead of proceeding directly to final seal.
- `F02 [P2]` fixed: Slice 02 now names `_drafts` implementation guides
  explicitly.

### skeleton-doc-r15

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-seal-a4

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude seal half: `VERDICT: 2 findings`, `EXIT=0`.
- Outcome: seal broken; fixed both findings and returned to the Codex loop.
- `F01 [P2]` fixed: Reuse Posture now explains how broad reviewer invocation
  extends the existing deviation path into a reviewed common rule.
- `F02 [P2]` fixed: Shared Contract now separates brainstorming exploration
  from `_drafts` implementation guides and limits Adopt / Revise / Reject to
  relevant guide decisions or operator-named planning material.

### skeleton-doc-r16

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`.

- `F01 [P1]` fixed: Slice 03 now includes independent seal reviewer selection,
  fallback handling, and usable-output evidence rules in addition to bypass,
  no-edit, and egress.

### skeleton-doc-r17

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`.

- `F01 [P1]` fixed: continuation now returns to documentation review after the
  r16 fix instead of proceeding directly to final seal.

### skeleton-doc-r18

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-seal-a5

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude seal half: `VERDICT: 1 finding`, `EXIT=0`.
- Outcome: seal broken; fixed the finding and returned to the Codex loop.
- `F01 [P2]` fixed: Shared Contract and Reuse Posture now state the common
  default can be broad tool-enabled review, while stricter local-context
  read-only or redacted-review rules win for sensitive consumers.

### skeleton-doc-r19

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`.

- `F01 [P1]` fixed: continuation now returns to documentation review after the
  seal-a5 fix instead of proceeding directly to final seal.

### operator-correction

Operator clarified that Tutor's current read-only/security posture is stale and
must not drive the common access default. S2 keeps Tutor as a process-shape and
reviewer-independence reference, but the common review invocation direction is
broad bypass/tool-enabled review for Codex and Claude, with explicit local
exclusions supplied by `local-context.md`.

### skeleton-doc-r20

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-seal-a6

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude seal half: `VERDICT: 2 findings`, `EXIT=0`.
- Outcome: seal broken; fixed both findings and returned to the Codex loop.
- `F01 [P1]` fixed: Shared Contract and Reuse Posture now say broad review is
  the S2 target common default; until Slice 03 seals, it remains an S2-local
  deviation from the current `v0.2.0` read-only baseline.
- `F02 [P2]` fixed: seal reviewer independence/fallback moved into its own
  planned Slice 04.

### skeleton-doc-r21

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-seal-a7

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude seal half: `VERDICT: 2 findings`, `EXIT=0`.
- Outcome: seal broken; fixed both findings and returned to the Codex loop.
- `F01 [P2]` fixed: Shared Contract and Reuse Posture now distinguish current
  common canon from S2 target rules that become canon only after their planned
  slices seal.
- `F02 [P3]` fixed: the skeleton now has an explicit Non-Goals section for
  product overfit, closed S0/S1 outcomes, runner tooling, and local-context
  boundaries.

### skeleton-doc-r22

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`.

- `F01 [P2]` fixed: Reuse Posture now names the Slice 04 seal reviewer
  independence/fallback/usable-output evidence rule family as new machinery.

### skeleton-doc-r23

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-seal-a8

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude seal half: `VERDICT: 1 finding`, `EXIT=0`.
- Outcome: seal broken; fixed the finding and returned to the Codex loop.
- `F01 [P2]` fixed: Shared Contract now names Slice 04's seal reviewer
  independence, fallback handling, and usable-output evidence targets.

### skeleton-doc-r24

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`.

### skeleton-doc-seal-a9

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude seal half: `VERDICT: 2 findings`, `EXIT=0`.
- Outcome: seal broken; fixed both findings and returned to the Codex loop.
- `F01 [P1]` fixed: the S2 broad/bypass reviewer invocation deviation is now
  mirrored in `implementation/process/codex-review.md` and linked from the
  milestone's Canonical Basis.
- `F02 [P2]` fixed: this log now records durable worktree no-change evidence
  for broad/bypass review rounds and seal halves used after the current
  no-edit attestation requirement was added.

### broad-invocation-worktree-evidence

All saved broad/bypass review outputs from `skeleton-doc-r22` onward record
`EXIT=0` and matching `WORKTREE BEFORE` / `WORKTREE AFTER` snapshots. The
matching snapshots show no reviewer-created tracked or untracked non-ignored
changes. Earlier clean rounds without saved snapshot blocks were superseded by
later skeleton fixes and are not used as current seal evidence.

- `skeleton-doc-r22`: matched snapshots.
- `skeleton-doc-r23`: matched snapshots.
- `skeleton-doc-r24`: matched snapshots.
- `skeleton-doc-r25`: matched snapshots.
- `skeleton-doc-r26`: matched snapshots.
- `skeleton-doc-seal-a7-codex`: matched snapshots.
- `skeleton-doc-seal-a7-claude`: matched snapshots.
- `skeleton-doc-seal-a8-codex`: matched snapshots.
- `skeleton-doc-seal-a8-claude`: matched snapshots.
- `skeleton-doc-seal-a9-codex`: matched snapshots.
- `skeleton-doc-seal-a9-claude`: matched snapshots.
- `skeleton-doc-seal-a10-codex`: matched snapshots.
- `skeleton-doc-seal-a10-claude`: matched snapshots.
- `skeleton-doc-seal-a11-codex`: matched snapshots.
- `skeleton-doc-seal-a11-claude`: matched snapshots.

### skeleton-doc-r25

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`, and matching
worktree before/after snapshots.

### skeleton-doc-seal-a10

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude seal half: `VERDICT: 2 findings`, `EXIT=0`.
- Outcome: seal broken; fixed both findings and returned to the Codex loop.
- `F01 [P3]` fixed: Current Slice now says the skeleton must seal and be
  committed before Slice 01 is drafted.
- `F02 [P3]` fixed: the local deviation register now records the temporary
  broad/bypass deviation exit condition.

### skeleton-doc-r26

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`, and matching
worktree before/after snapshots.

### skeleton-doc-seal-a11

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude CLI seal half: `VERDICT: 0 findings`, `EXIT=0`, using
  `claude -p --model opus --effort max --permission-mode bypassPermissions`.
- Outcome: skeleton documentation sealed `ready`; no accepted debt.

## Slice 01 Documentation

### slice-01-doc-r1

Codex review completed with `VERDICT: 2 findings`, `EXIT=0`, and matching
worktree before/after snapshots.

- `F01 [P1]` fixed: support-order/platform-preference constraints now apply to
  milestone skeletons as well as slice notes, consultations, reviews, and
  implementation decisions.
- `F02 [P2]` fixed: the pre-seal gate now blocks changes to any Slice 01
  expected implementation file until the slice note seals `ready` and is
  committed.

### slice-01-doc-r2

Codex review completed with `VERDICT: 2 findings`, `EXIT=0`, and matching
worktree before/after snapshots.

- `F01 [P1]` fixed: `canon/process/codex-review.md` is now in scope and tests,
  so review prompt guidance must load and enforce local context when relevant.
- `F02 [P2]` fixed: acceptance criteria now require implementation decisions to
  apply local support-order or platform-preference constraints before proposing
  new machinery.

### slice-01-doc-r3

Codex review completed with `VERDICT: 2 findings`, `EXIT=0`, and matching
worktree before/after snapshots.

- `F01 [P2]` fixed: the milestone slice table now marks Slice 01 as
  `review_requested`, matching the active slice note and work log.
- `F02 [P2]` fixed: the test plan now checks required local-context template
  sections, the full sensitive-data warning, and this repository's
  product-neutral/no-support-order local context.

### slice-01-doc-r4

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`, and matching
worktree before/after snapshots.

- `F01 [P2]` fixed: milestone and slice templates are now expected files and
  tests require them to reference `local-context.md` when authors fill Reuse
  Posture for new machinery.

### slice-01-doc-r5

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`, and matching
worktree before/after snapshots.

- `F01 [P2]` fixed: tests now target each required surface: Reuse Posture,
  milestone skeletons, slice notes, consultations, reviews, implementation
  decisions, and new-machinery proposals.

### slice-01-doc-r6

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`, and matching
worktree before/after snapshots.

- `F01 [P2]` fixed: tests now directly verify the canon-side guard that local
  context is local constraints, not process authority, and that temporary
  process deviations remain in `implementation/process/*`.

### slice-01-doc-r7

Codex review completed with `VERDICT: 2 findings`, `EXIT=0`, and matching
worktree before/after snapshots.

- `F01 [P2]` fixed: tests now reject Agent99/Tutor/LPC/Life/Firebase product
  names in common canon and local-state templates.
- `F02 [P2]` fixed: tests now check `local-context.md` inside the Required
  Local Layout block, not merely anywhere in `canon/process/README.md`.

### slice-01-doc-r8

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`, and matching
worktree before/after snapshots.

- `F01 [P2]` fixed: the Required Local Layout test now uses executable awk
  slash escaping.

### slice-01-doc-r9

Codex review completed with `VERDICT: 1 finding`, `EXIT=0`, and matching
worktree before/after snapshots.

- `F01 [P1]` rejected after Claude CLI adjudication
  (`slice-01-doc-r9-f01-adjudication`, `EXIT=0`): the local-context template
  section and no-raw-secrets warning define file shape and data hygiene, not
  review access, egress, or invocation posture. Slice 03 still owns broad
  reviewer invocation and egress behavior.

### slice-01-doc-seal-a1

- Codex seal half: `VERDICT: 1 finding`, `EXIT=0`.
- Claude CLI seal half: `VERDICT: 0 findings`, `EXIT=0`, using
  `claude -p --model opus --effort max --permission-mode bypassPermissions`.
- Outcome: seal broken; fixed the Codex finding and returned to the Codex loop.
- `F01 [P2]` fixed: the Slice 01 work-log row now uses `review_requested` for
  a pending seal/review state instead of undefined `seal_requested`.

### slice-01-doc-r10

Codex review completed with `VERDICT: 2 findings`, `EXIT=0`, and matching
worktree before/after snapshots.

- `F01 [P2]` fixed: the product-name guard now also covers this repository's
  required `implementation/local-context.md`.
- `F02 [P2]` fixed: tests now preserve the current common Codex invocation
  posture while broad reviewer invocation remains deferred to Slice 03.

### slice-01-doc-r11

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`, and matching
worktree before/after snapshots.

### slice-01-doc-seal-a2

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude CLI seal half: `VERDICT: 1 finding`, `EXIT=0`, using
  `claude -p --model opus --effort max --permission-mode bypassPermissions`.
- Outcome: seal broken; fixed the Claude finding and returned to the Codex
  loop.
- `F01 [P2]` fixed: Reuse Posture now explains that support-order and
  platform-preference enforcement extends the existing Reuse Gate and Reviews
  model instead of adding a parallel approval path.

### slice-01-doc-r12

Codex review completed with `VERDICT: 0 findings`, `EXIT=0`, and matching
worktree before/after snapshots.

### slice-01-doc-seal-a3

- Codex seal half: `VERDICT: 0 findings`, `EXIT=0`.
- Claude CLI seal half: `VERDICT: 0 findings`, `EXIT=0`, using
  `claude -p --model opus --effort max --permission-mode bypassPermissions`.
- Outcome: Slice 01 documentation sealed `ready`; no accepted debt.

## Slice 01 Implementation

Pending.
