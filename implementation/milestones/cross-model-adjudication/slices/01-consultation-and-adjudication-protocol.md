# Slice 01 - Consultation And Adjudication Protocol

Status: ready

## Scope

Amend the common process canon so review findings, doubts, disagreements,
cross-model consultation, adjudication, and operator escalation are explicit.

In scope:

- `canon/process/README.md`
- `canon/process/codex-review.md`
- root `README.md` pinning guidance.
- `VERSION`
- template compatibility check for `templates/local-state/**`.
- local S1 state under `implementation/`.

## Non-Goals

- Add automation, scripts, or review runners.
- Change the milestone/slice hierarchy.
- Change the S0 record or rewrite `v0.1.1`.
- Migrate Agent99 or Tutor.
- Make a reviewer, sub-agent, or consulted LLM the adjudicator.
- Change template files unless review proves their canon pointers cannot inherit
  the new protocol.

## Reuse Posture

- Checked: existing Review, Saving Output, Prompt Shape, and local S0 process
  records.
- Reused or extended: the existing triage outcomes, review-log evidence model,
  double seals, and operator-accepted debt rules.
- New machinery, if any: explicit consultation/adjudication protocol language
  only.
- Compatibility: existing consumers keep working; the next tag adds stricter
  review governance.

## Dependencies

- S1 skeleton sealed and committed at `525a691`.
- Codex CLI available for review rounds.
- Claude available as the different-family seal/consultation counterpart for
  this repo while Codex orchestrates.
- Existing reviewed tag `v0.1.1` remains immutable.

## Expected Files

- `canon/process/README.md`
- `canon/process/codex-review.md`
- `README.md`
- `VERSION`
- `templates/local-state/**` (checked for compatibility; no change expected)
- `implementation/milestones/cross-model-adjudication/**`

## Acceptance Criteria

- The canon explicitly says reviewer findings are claims/evidence, not facts.
- The canon explicitly requires the orchestrator to verify every finding against
  files, diffs, tests, or commands before triage.
- The canon explicitly forbids triage from memory, chat, or prior review output
  without direct artifact evidence.
- The canon keeps triage authority with the orchestrator.
- The canon requires cross-family LLM discussion for doubts and disagreements
  when such a counterpart is available, including when the doubt came from a
  same-family sub-agent.
- If cross-family discussion is unavailable or does not resolve the issue, the
  process stops and asks the operator.
- `P0`/`P1` findings cannot become debt; `P2`/`P3` debt still requires explicit
  operator acceptance.
- Review prompt guidance tells reviewers and orchestrators what evidence and
  output to preserve.
- Template compatibility is checked: local-state process templates keep pointing
  at the common canon and do not duplicate the protocol.
- `VERSION` advances to `0.2.0`, and public pinning guidance points to
  `v0.2.0`.
- The implementation double seal has independent Codex and Claude clean halves.
- S1 implementation finding triage follows the new verification,
  cross-family-discussion, and operator-escalation protocol before closure.
- Closure records reviewed content commit and planned tag.

## Release Sequence

1. Commit the sealed Slice 01 note, then commit the local continuation/work-log
   bookkeeping that marks Slice 01 documentation `ready`.
2. Apply canon docs, `VERSION`, and public pinning changes; commit the reviewed
   content commit.
3. Run implementation review and double final seal on that content commit,
   using the new verification, cross-family-discussion, and
   operator-escalation protocol for S1 findings.
4. Add closure/bookkeeping updates recording the reviewed content commit and
   planned tag; commit the final release commit.
5. Create annotated tag `v0.2.0` on the final release commit.
6. Push `main` and `v0.2.0`.

## Pre-Tag Tests

- `git diff --check`
- `test "$(cat VERSION)" = "0.2.0"`
- `rg -n "checkout v0.2.0" README.md`
- `rg -n "reviewer findings are claims" canon/process/README.md`
- `rg -n "files, diffs, tests, or commands" canon/process/README.md`
- `rg -n "memory or chat" canon/process/README.md`
- `rg -n "different LLM family" canon/process/README.md`
- `rg -n "same-family sub-agent" canon/process/README.md`
- `rg -n "stop and consult the operator|stops and asks the operator" canon/process/README.md`
- `rg -n "files, diffs, tests, or commands" canon/process/codex-review.md`
- `rg -n "reviewer findings are claims" canon/process/codex-review.md`
- `rg -n "different LLM family" canon/process/codex-review.md`
- `rg -n "same-family sub-agent" canon/process/codex-review.md`
- `rg -n "stop and consult the operator|stops and asks the operator" canon/process/codex-review.md`
- `rg -n "common .*canon|canon/process" templates/local-state/implementation/process`
- `! rg -n "reviewer findings are claims|same-family sub-agent|different LLM family" templates/local-state`
- `test "$(git rev-parse 'v0.1.1^{tag}')" = "9fd0945ee09d6d73230f4696c77e8f865eb606bd"`
- `test "$(git ls-remote origin refs/tags/v0.1.1 | awk '{print $1}')" = "9fd0945ee09d6d73230f4696c77e8f865eb606bd"`
- `test "$(git rev-list -n 1 v0.1.1)" = "d51c7f0f68d36b02495218498208a29cd5aa6217"`
- `test "$(git ls-remote origin 'refs/tags/v0.1.1^{}' | awk '{print $1}')" = "d51c7f0f68d36b02495218498208a29cd5aa6217"`

## Post-Tag Tests

- `test "$(git rev-list -n 1 v0.2.0)" = "$(git rev-parse HEAD)"`
- `test "$(git show v0.2.0:VERSION)" = "0.2.0"`

## Risks

- Over-specifying the protocol could make simple review findings too heavy.
  Mitigation: require cross-family discussion for doubts/disagreements, while
  straightforward verified findings can still be fixed directly.
- Under-specifying fallback could let the orchestrator reject findings alone.
  Mitigation: unresolved disagreement stops for the operator.

## Review

This slice note must seal `ready` and be committed before canon changes begin.
