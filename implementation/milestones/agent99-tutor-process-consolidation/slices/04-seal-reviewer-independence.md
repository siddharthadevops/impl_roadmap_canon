# Slice 04 - Seal Reviewer Independence

Status: ready

## Scope

Move the remaining S2 seal-reviewer rules into the common process canon.

In scope:

- double-seal reviewer independence.
- mandatory Codex seal half.
- Claude CLI as the required non-Codex seal half when Codex is the
  worker/orchestrator.
- no silent fallback from the required Claude CLI seal half.
- usable-output evidence rules for seal halves.
- Claude seal runtime guidance, including the boundary between Codex watchdogs
  and Claude's 30-minute availability window.
- S2 local closeout state after implementation.
- reviewed release `v0.3.0` for the completed S2 canon.

## Non-Goals

- Do not change broad review invocation, worktree checks, or egress boundaries;
  Slice 03 owns those.
- Do not add product names, support names, stack choices, or Tutor's stale
  read-only access posture to the common canon.
- Do not add automation or new review tooling.
- Do not make reviewer settings-only differences count as independence.

## Reuse Posture

- Checked: common review cycle, common review runner, S1 cross-family
  adjudication rules, Agent99/Tutor reviewer-independence wording, and Tutor's
  Claude CLI usable-output and fallback safeguards.
- Reused or extended: the existing double final seal, Codex mandatory seal
  half, Claude CLI command shape from Slice 03, cross-family consultation
  principle, and worktree invalidation.
- New machinery, if any: no new tooling; only explicit common rules for the
  non-Codex seal half, fallback authorization, and usable seal evidence.
- Compatibility: consumers can keep the same review scratch and review-log
  layout. If the required independent reviewer is unavailable, the process
  stops unless the operator explicitly authorizes a fallback for that attempt.
- Local context: no product support order is recorded; no sensitive local
  exclusions are recorded for this repository.

## Dependencies

- S2 Slice 03 closed at `89d7b70`.
- Codex CLI available for documentation review rounds and one seal half.
- Claude CLI available for the non-Codex seal half when Codex is the
  worker/orchestrator.

## Expected Files

- `canon/process/README.md`
- `canon/process/codex-review.md`
- `README.md`
- `VERSION`
- `implementation/roadmap.md`
- `implementation/milestones/README.md`
- `implementation/milestones/agent99-tutor-process-consolidation/README.md`
- `implementation/milestones/agent99-tutor-process-consolidation/review-log.md`
- `implementation/milestones/agent99-tutor-process-consolidation/closures/README.md`
- `implementation/milestones/agent99-tutor-process-consolidation/closures/04-seal-reviewer-independence.md`

## Acceptance Criteria

- The common cycle says the double final seal uses two independent reviewers on
  an unchanged artifact.
- Codex remains one mandatory seal half.
- The other seal half must run in a fresh independent context, not the thread
  or agent that drafted or implemented the artifact.
- Both seal halves must receive the same review prompt and neither half may see
  the other half's output before both have completed.
- Codex seal output is usable only with `EXIT=0`, a `VERDICT:` line, a verdict
  count matching captured `Fxx [Pn]` findings, no worktree invalidation marker,
  and the reviewed artifact unchanged.
- When Codex is the worker/orchestrator, the non-Codex seal half must run
  through Claude CLI using
  `claude -p --model opus --effort max --permission-mode bypassPermissions`.
- The common canon requires Claude CLI seal output to record the reviewer,
  model/settings, command surface, result, and `EXIT=`.
- Claude CLI seal output is usable only with `EXIT=0`, a `VERDICT:` line, a
  verdict count matching captured `Fxx [Pn]` findings, no worktree invalidation
  marker, and the reviewed artifact unchanged.
- Claude CLI seal runs must allow at least 30 minutes before silence or normal
  long runtime can be classified as unavailable.
- The existing 480-second watchdog remains a Codex-review watchdog only; Claude
  seal instructions must not apply that 480-second kill window to Claude.
- The common canon explicitly forbids restricted Claude seal modes such as
  `--safe-mode`, `--tools ''`, and `--permission-mode plan`.
- If the required Claude CLI seal half is unavailable, the seal remains
  incomplete unless the operator explicitly authorizes a fallback for that seal
  attempt.
- Any authorized fallback must be an independent non-Codex reviewer whose base
  model family differs from the mandatory Codex seal half; settings-only
  differences are insufficient.
- A Codex-hosted sub-agent or OpenAI/GPT-family reviewer cannot replace the
  required non-Codex seal half for a Codex-orchestrated seal.
- Fallback records must include reviewer, model/settings, command surface,
  reason, operator authorization, and result.
- Authorized fallback output must meet the same usable seal-output rules as the
  required non-Codex seal half: `EXIT=0`, `VERDICT:`, count consistency, no
  worktree invalidation marker, and unchanged artifact.
- The common canon remains product-neutral and does not copy Tutor's stale
  read-only access default.
- After Slice 04 implementation and closure, S2 live local state is closed:
  the milestone status, Slice 04 table row, current slice, continuation, work
  log, review log, and closure records show no active S2 work. Historical
  sealed skeleton sections are not rewritten unless explicitly reopened.
- The global continuation no longer points to an active S2 slice.
- The roadmap closeout summarizes that S2 moved reusable process rules into the
  common canon while leaving live project state local.
- `VERSION` advances to `0.3.0`, and public pinning guidance points to
  `v0.3.0`.
- Slice 04 closure records the reviewed content commit and planned reviewed tag
  `v0.3.0`.
- The reviewed tag `v0.3.0` is created on the final release commit and pushed
  with `main`.
- The final release commit after the reviewed content commit contains only
  closure/bookkeeping changes. Any substantive canon, README, `VERSION`, or
  roadmap change after implementation seal reopens implementation review.

## Release Sequence

1. Commit the sealed Slice 04 note, then commit local documentation
   bookkeeping that marks Slice 04 documentation `ready`.
2. Apply common canon, `VERSION`, README pinning, and roadmap closeout changes;
   commit the reviewed content commit.
3. Run implementation review and double final seal on that content commit.
4. Add closure/bookkeeping updates recording the reviewed content commit and
   planned tag; commit the final release commit.
5. Create annotated tag `v0.3.0` on the final release commit.
6. Push `main` and `v0.3.0`.

## Pre-Tag Tests

- `git diff --check`
- `test "$(cat VERSION)" = "0.3.0"`
- `rg -n "checkout v0.3.0" README.md`
- `! rg -n "checkout v0.2.0" README.md`
- `rg -n "two independent reviewers|independent reviewers" canon/process/README.md canon/process/codex-review.md`
- `rg -n "unchanged artifact" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Codex.*mandatory seal half|mandatory Codex seal half|Codex remains.*seal half" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fresh independent context|fresh, independent context|not the thread.*drafted|not.*drafted or implemented" canon/process/README.md canon/process/codex-review.md`
- `rg -n "same review prompt|same prompt" canon/process/README.md canon/process/codex-review.md`
- `rg -n "neither.*other.*output|without seeing.*other.*output|do not.*see.*other" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Codex seal.*EXIT=0|EXIT=0.*Codex seal" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Codex seal.*VERDICT|VERDICT.*Codex seal" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Codex seal.*count|count.*Codex seal|Codex seal.*finding-count" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Codex seal.*worktree invalidation|worktree invalidation.*Codex seal|Codex seal.*INVALID" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Codex seal.*unchanged artifact|unchanged artifact.*Codex seal" canon/process/README.md canon/process/codex-review.md`
- `rg -n "worker/orchestrator" canon/process/README.md canon/process/codex-review.md`
- `rg -n "claude -p --model opus --effort max --permission-mode bypassPermissions" canon/process/codex-review.md`
- `rg -n "Claude CLI reviewer|Claude.*reviewer" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude.*model/settings|model/settings.*Claude" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude.*command surface|command surface.*Claude" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude.*result|result.*Claude" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude.*EXIT=|EXIT=.*Claude" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude CLI seal.*EXIT=0|EXIT=0.*Claude CLI seal|Claude.*seal.*EXIT=0" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude CLI seal.*VERDICT|VERDICT.*Claude CLI seal|Claude.*seal.*VERDICT" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude CLI seal.*count|count.*Claude CLI seal|Claude.*seal.*finding-count" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude CLI seal.*worktree invalidation|worktree invalidation.*Claude CLI seal|Claude.*seal.*INVALID" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude CLI seal.*unchanged artifact|unchanged artifact.*Claude CLI seal|Claude.*seal.*unchanged artifact" canon/process/README.md canon/process/codex-review.md`
- `rg -n "EXIT=0" canon/process/codex-review.md`
- `rg -n "VERDICT:" canon/process/codex-review.md`
- `rg -n "verdict count.*captured|captured.*verdict count|finding-count" canon/process/codex-review.md`
- `rg -n "INVALID: worktree changed|worktree invalidation" canon/process/codex-review.md`
- `rg -n "30 minutes|at least 30" canon/process/README.md canon/process/codex-review.md`
- `rg -n "480-second watchdog.*Codex|Codex.*480-second watchdog|Codex-review watchdog" canon/process/codex-review.md`
- `rg -n "480-second watchdog.*does not apply.*Claude|Claude.*does not apply.*480-second watchdog|480-second watchdog.*Codex-only" canon/process/codex-review.md`
- `! rg -n "Claude.*sleep 480|sleep 480.*Claude|Claude.*kill.*480|480.*kill.*Claude" canon/process/codex-review.md`
- `rg -n -- "Do not use.*--safe-mode|forbid.*--safe-mode|prohibit.*--safe-mode|--safe-mode.*restricted" canon/process/README.md canon/process/codex-review.md`
- `rg -n -- "Do not use.*--tools ''|forbid.*--tools ''|prohibit.*--tools ''|--tools ''.*restricted" canon/process/README.md canon/process/codex-review.md`
- `rg -n -- "Do not use.*--permission-mode plan|forbid.*--permission-mode plan|prohibit.*--permission-mode plan|--permission-mode plan.*restricted" canon/process/README.md canon/process/codex-review.md`
- `rg -n "not silently fall back|no silent fallback|do not silently fall back" canon/process/README.md canon/process/codex-review.md`
- `rg -n "operator explicitly authorizes|operator authorization" canon/process/README.md canon/process/codex-review.md`
- `rg -n "base model family" canon/process/README.md canon/process/codex-review.md`
- `rg -n "settings-only differences" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Codex-hosted" canon/process/README.md canon/process/codex-review.md`
- `rg -n "OpenAI/GPT-family|GPT-family" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback reviewer|fallback.*reviewer" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback.*model/settings|model/settings.*fallback" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback.*command surface|command surface.*fallback" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback.*reason|reason.*fallback" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback.*operator authorization|operator authorization.*fallback" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback.*result|result.*fallback" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback.*EXIT=0|EXIT=0.*fallback" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback.*VERDICT|VERDICT.*fallback" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback.*count consistency|fallback.*finding-count|count consistency.*fallback" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback.*worktree invalidation|worktree invalidation.*fallback|fallback.*INVALID" canon/process/README.md canon/process/codex-review.md`
- `rg -n "fallback.*unchanged artifact|unchanged artifact.*fallback" canon/process/README.md canon/process/codex-review.md`
- `! rg -n "Agent99|Tutor|LPC|Life|Firebase|Phoenix|Elixir" canon/process/README.md canon/process/codex-review.md`
- `! rg -n "codex exec --sandbox read-only|read-only.*default|default.*read-only" canon/process/README.md canon/process/codex-review.md`
- `! rg -n "fresh, read-only context|fresh read-only context|read-only context" canon/process/README.md canon/process/codex-review.md`
- `rg -n "S2 .*Closed|S2 .*closed|Status: closed" implementation/milestones/README.md implementation/milestones/agent99-tutor-process-consolidation/README.md`
- `rg -n "\\| S2 \\| Agent99/Tutor process consolidation \\| Process canon \\| Closed \\(reviewed release \`v0.3.0\`\\)" implementation/milestones/README.md`
- `rg -n "^Status: closed$" implementation/milestones/agent99-tutor-process-consolidation/README.md`
- `! rg -n "^Status: open" implementation/milestones/agent99-tutor-process-consolidation/README.md`
- `rg -n "\\| 04 \\| Seal reviewer independence \\| closed \\|" implementation/milestones/agent99-tutor-process-consolidation/README.md`
- `rg -n "\\| [0-9]+ \\| Slice 04 \\| closure \\| closed \\|" implementation/milestones/agent99-tutor-process-consolidation/README.md`
- `awk '/^## Current Slice/{p=1; next} /^## /{p=0} p' implementation/milestones/agent99-tutor-process-consolidation/README.md | rg -n "None|closed"`
- `awk '/^## Continuation/{p=1; next} /^## /{p=0} p' implementation/milestones/agent99-tutor-process-consolidation/README.md | rg -n "closed|global milestone index|roadmap"`
- `! awk '/^## Current Slice/{p=1; next} /^## /{p=0} p' implementation/milestones/agent99-tutor-process-consolidation/README.md | rg -n "Slice 04 documentation|Slice 04 implementation|Open"`
- `! awk '/^## Continuation/{p=1; next} /^## /{p=0} p' implementation/milestones/agent99-tutor-process-consolidation/README.md | rg -n "Slice 04 documentation|Slice 04 implementation|Open"`
- `rg -n "## Slice 04 Documentation" implementation/milestones/agent99-tutor-process-consolidation/review-log.md`
- `rg -n "## Slice 04 Implementation" implementation/milestones/agent99-tutor-process-consolidation/review-log.md`
- `rg -n "slice-04-impl-seal" implementation/milestones/agent99-tutor-process-consolidation/review-log.md`
- `test -f implementation/milestones/agent99-tutor-process-consolidation/closures/04-seal-reviewer-independence.md`
- `rg -n "04-seal-reviewer-independence.md|Slice 04 - Seal Reviewer Independence" implementation/milestones/agent99-tutor-process-consolidation/closures/README.md`
- `rg -n "Status: closed" implementation/milestones/agent99-tutor-process-consolidation/closures/04-seal-reviewer-independence.md`
- `rg -n "Review state:.*review_clean|review_clean.*Review state" implementation/milestones/agent99-tutor-process-consolidation/closures/04-seal-reviewer-independence.md`
- `awk '/^## Active Continuation/{p=1; next} /^## /{p=0} p' implementation/milestones/README.md | rg -n "No active milestone|no active milestone|future canon change|Future canon change"`
- `! awk '/^## Active Continuation/{p=1; next} /^## /{p=0} p' implementation/milestones/README.md | rg -n "S2|agent99-tutor-process-consolidation|current unit|Slice 04"`
- `rg -n "S2.*common process|common process.*S2" implementation/roadmap.md`
- `rg -n "reviewed release.*v0.3.0|v0.3.0.*reviewed release" implementation/roadmap.md`
- `rg -n "live project state.*local|local.*live project state" implementation/roadmap.md`
- `rg -n "Planned reviewed tag: \`v0.3.0\`" implementation/milestones/agent99-tutor-process-consolidation/closures/04-seal-reviewer-independence.md`
- `reviewed_commit=$(awk -F'\`' '/Reviewed content commit/{print $2; exit}' implementation/milestones/agent99-tutor-process-consolidation/closures/04-seal-reviewer-independence.md); test -n "$reviewed_commit" && git cat-file -e "$reviewed_commit^{commit}" && test -z "$(git diff --name-only "$reviewed_commit"..HEAD | rg -v '^(implementation/milestones/README.md|implementation/milestones/agent99-tutor-process-consolidation/README.md|implementation/milestones/agent99-tutor-process-consolidation/review-log.md|implementation/milestones/agent99-tutor-process-consolidation/closures/README.md|implementation/milestones/agent99-tutor-process-consolidation/closures/04-seal-reviewer-independence.md)$')"`

## Post-Tag Tests

- `test "$(git rev-list -n 1 v0.3.0)" = "$(git rev-parse HEAD)"`
- `test "$(git show v0.3.0:VERSION)" = "0.3.0"`
- `git rev-parse "v0.3.0^{tag}"`
- `test "$(git ls-remote origin refs/heads/main | awk '{print $1}')" = "$(git rev-parse HEAD)"`
- `test "$(git ls-remote origin refs/tags/v0.3.0 | awk '{print $1}')" = "$(git rev-parse "v0.3.0^{tag}")"`
- `test "$(git ls-remote origin 'refs/tags/v0.3.0^{}' | awk '{print $1}')" = "$(git rev-list -n 1 v0.3.0)"`

## Risks

- A same-family or drafting-context reviewer could appear independent. Mitigation:
  independence requires a fresh context and, for Codex-orchestrated seals, the
  non-Codex half is Claude CLI unless the operator authorizes a fallback.
- Fallback could hide reviewer unavailability. Mitigation: no silent fallback;
  incomplete seals stop unless the operator authorizes that attempt's fallback.
- Malformed seal output could be treated as evidence. Mitigation: usable output
  requires `EXIT=0`, `VERDICT:`, count consistency, unchanged artifact, and no
  worktree invalidation.

## Review

This slice note must seal `ready` and be committed before any Slice 04 expected
file is changed for implementation.
