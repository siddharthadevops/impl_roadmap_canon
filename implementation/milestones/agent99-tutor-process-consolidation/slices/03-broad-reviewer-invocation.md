# Slice 03 - Broad Reviewer Invocation

Status: ready

## Scope

Move the S2 broad/bypass reviewer invocation deviation into the common review
canon for Codex and Claude review commands.

In scope:

- default Codex CLI review command.
- Claude CLI full-access review command shape when Claude is invoked.
- no-edit prompt requirement for every broad reviewer run.
- before/after worktree mutation checks.
- relevance-driven sibling/dependency inspection.
- egress and sensitive-data boundaries tied to local context.
- removal of this repository's temporary local broad/bypass deviation.
- S2 local state and review records.

## Non-Goals

- Do not change seal reviewer independence, mandatory reviewer selection,
  fallback handling, or usable-output evidence rules; Slice 04 owns those.
- Do not add product examples, support names, stack choices, or Tutor's stale
  read-only access posture to the common canon.
- Do not require prompts to list every directory a reviewer may need.
- Do not allow reviewers to edit files merely because the CLI has broad access.

## Reuse Posture

- Checked: current common `codex-review.md`, this repository's temporary S2
  deviation, Agent99 full-access review runner, and Tutor's Claude CLI command
  shape plus egress hard-exclusion wording. Tutor's read-only access default is
  stale for this common rule; its never-send egress floor remains reusable.
- Reused or extended: Agent99's full-access Codex invocation, no-edit prompt
  requirement, worktree invalidation check, and relevance-driven inspection
  model; Tutor's Claude CLI bypass command shape and never-send/redacted-excerpt
  egress boundary.
- New machinery, if any: common full-access review mode for Codex and Claude
  review commands, with local-context exclusions and worktree mutation
  invalidation.
- Compatibility: consuming projects with stricter needs record explicit
  exclusions in local context or a local process deviation; those local
  constraints win over broad access.
- Local context: no product support order is recorded; no sensitive local
  exclusions are recorded for this repository.

## Dependencies

- S2 Slice 02 closed at `c4de17a`.
- Codex CLI available for documentation review rounds.
- Claude CLI available when the existing review or seal process invokes Claude.
- The S2 temporary broad/bypass reviewer deviation remains active only for this
  slice's reviews until this slice seals or records a different disposition.

## Expected Files

- `canon/process/codex-review.md`
- `implementation/process/codex-review.md`
- `implementation/milestones/README.md`
- `implementation/milestones/agent99-tutor-process-consolidation/README.md`
- `implementation/milestones/agent99-tutor-process-consolidation/review-log.md`

## Acceptance Criteria

- The common Codex review invocation defaults to
  `codex exec --dangerously-bypass-approvals-and-sandbox`.
- The common canon no longer presents `codex exec --sandbox read-only` as the
  default review runner.
- The common canon no longer says broader filesystem access is a temporary local
  deviation or something that must be recorded before reviews can use it;
  stricter local exclusions and stricter local process deviations still win.
- The common canon names the Claude CLI full-access review command as
  `claude -p --model opus --effort max --permission-mode bypassPermissions`
  when Claude review commands are invoked.
- The common canon does not add mandatory Claude seal selection, seal reviewer
  independence, or different-family seal-counterpart rules; Slice 04 owns those.
- Broad CLI access is explicitly review-only: prompts must tell the reviewer not
  to edit, create, delete, move, format, or write files.
- A broad reviewer run must compare worktree state before and after the run.
  If tracked or untracked non-ignored files change, the output is invalid and
  does not count as review or seal evidence.
- The worktree check covers pre-existing dirty state, staged changes, and
  untracked non-ignored files; it is not only a clean-tree status check.
- The worktree check captures content hashes for pre-existing untracked
  non-ignored files, so a reviewer cannot modify such a file without
  invalidating the output.
- The common prompt shape tells reviewers to inspect sibling repositories or
  dependency checkouts only when relevant to the artifact and discovered while
  tracing it; prompts do not need to enumerate every possible directory.
- The common egress rule says review CLIs send read material to external
  services, local `Sensitive Local Exclusions` must be honored, unrelated
  personal material must be avoided, and secrets, credentials, tokens, private
  keys, raw PII, and raw sensitive operational data must never be sent.
- Operator confirmation does not override the never-send categories. If a
  review appears to require other sensitive material, the process must stop for
  operator confirmation or use redacted non-sensitive excerpts.
- This repository's local process review file no longer records an active
  temporary broad/bypass deviation after the common rule is implemented.
- S2 local active state no longer instructs reviewers to use, or presents the
  active unit as needing, the temporary S2 broad/bypass deviation after the
  common rule is implemented. Historical sealed skeleton sections are not
  rewritten unless that documentation is explicitly reopened.
- The common canon remains product-neutral and does not copy Tutor's stale
  read-only default.

## Tests

- `git diff --check`
- `rg -n "codex exec --dangerously-bypass-approvals-and-sandbox" canon/process/codex-review.md`
- `! rg -n "codex exec --sandbox read-only" canon/process/codex-review.md`
- `! rg -n "temporarily needs broader filesystem access|broader filesystem access.*deviation|record that deviation in local state" canon/process/codex-review.md`
- `rg -n "claude -p --model opus --effort max --permission-mode bypassPermissions" canon/process/codex-review.md`
- `rg -n "review-only|review only" canon/process/codex-review.md`
- `rg -n "must not edit|must not modify|must not.*write" canon/process/codex-review.md`
- `rg -n "must not.*create.*file|not.*create.*file|create, delete, move, format" canon/process/codex-review.md`
- `rg -n "must not.*delete.*file|not.*delete.*file|create, delete, move, format" canon/process/codex-review.md`
- `rg -n "must not.*move.*file|not.*move.*file|create, delete, move, format" canon/process/codex-review.md`
- `rg -n "must not.*format.*file|not.*format.*file|create, delete, move, format" canon/process/codex-review.md`
- `rg -n "worktree.*before.*after|before.*after.*worktree" canon/process/codex-review.md`
- `rg -n "INVALID: worktree changed|worktree changed.*invalid" canon/process/codex-review.md`
- `rg -n "Claude.*worktree|worktree.*Claude" canon/process/codex-review.md`
- `rg -n "git status --porcelain" canon/process/codex-review.md`
- `rg -n "git diff --no-ext-diff --binary" canon/process/codex-review.md`
- `rg -n "git diff --cached --no-ext-diff --binary" canon/process/codex-review.md`
- `rg -n "git ls-files --others --exclude-standard" canon/process/codex-review.md`
- `rg -n "shasum -a 256|sha256sum" canon/process/codex-review.md`
- `rg -n "sibling|dependency" canon/process/codex-review.md`
- `rg -n "relevant|relevance-driven" canon/process/codex-review.md`
- `rg -n "external service|external services|send.*read|read material" canon/process/codex-review.md`
- `rg -n "Claude CLI.*external service|external service.*Claude CLI|review CLIs.*external services|review CLIs.*send.*read" canon/process/codex-review.md`
- `rg -n "Sensitive Local Exclusions|sensitive local exclusions" canon/process/codex-review.md`
- `rg -n "unrelated personal material" canon/process/codex-review.md`
- `rg -n "secrets" canon/process/codex-review.md`
- `rg -n "credentials" canon/process/codex-review.md`
- `rg -n "tokens" canon/process/codex-review.md`
- `rg -n "private keys" canon/process/codex-review.md`
- `rg -n "raw PII" canon/process/codex-review.md`
- `rg -n "raw sensitive operational data" canon/process/codex-review.md`
- `rg -n "operator confirmation.*not.*override|never-send.*operator confirmation" canon/process/codex-review.md`
- `rg -n "redacted non-sensitive excerpts" canon/process/codex-review.md`
- `rg -n "stricter local.*deviation|local process deviation.*win|local deviations.*win|stricter.*local process deviations" canon/process/codex-review.md`
- `rg -n "No local deviations are active" implementation/process/codex-review.md`
- `! rg -n "temporary broad/bypass|deviation expires when Slice 03" implementation/process/codex-review.md`
- `! rg -n "Agent99|Tutor|LPC|Life|Firebase|Phoenix|Elixir" canon/process/codex-review.md implementation/process/codex-review.md`
- `! rg -n "safe-mode|permission-mode plan|fallback handling|fallback reviewer|fallback.*reviewer|reviewer.*fallback|review.*substitute|substitute.*review|usable-output evidence|usable.*seal.*evidence|seal.*evidence.*usable|usable.*evidence|evidence.*usable|mandatory reviewer selection|mandatory.*reviewer|reviewer.*selection|seal reviewer independence|reviewer independence|independent seal reviewer|different-family seal counterpart|seal counterpart|mandatory.*Claude|Claude.*mandatory" canon/process/codex-review.md`
- `! rg -nU "S2\\s+only,\\s+use\\s+the\\s+operator-authorized\\s+broad\\s+reviewer\\s+invocation\\s+deviation|Open\\s+\\(Slice\\s+03\\s+documentation\\s+(review|seal)\\)|current\\s+unit\\s+is\\s+Slice\\s+03\\s+documentation\\s+(review|seal)|^Status:\\s+open\\s+\\(Slice\\s+03\\s+documentation\\s+(review|seal)\\)|^Slice\\s+03\\s+documentation\\s+(review|seal)\\.$" implementation/milestones/README.md implementation/milestones/agent99-tutor-process-consolidation/README.md`

## Risks

- Broad access could be mistaken for permission to mutate files. Mitigation:
  prompts must say review-only/no-edit and the runner invalidates any worktree
  mutation.
- Broad inspection could over-read unrelated material. Mitigation: inspection is
  relevance-driven and bounded by local exclusions and sensitive-data rules.
- Slice 03 could accidentally absorb Slice 04. Mitigation: final seal
  independence, fallback, and usable-output evidence remain explicit non-goals.

## Review

This slice note must seal `ready` and be committed before any Slice 03 expected
file is changed for implementation.
