# Slice 01 - Local Context And Support Order

Status: ready

## Scope

Add a required local context file to the common process and templates, and make
local support-order or platform-preference constraints enforceable by slice
notes, milestone skeletons, reviews, consultations, and implementation
decisions.

In scope:

- common process layout and reuse-gate language.
- local-state templates for consuming projects.
- this repository's own local context file.
- S2 local state and review records.

## Non-Goals

- Do not canonize Agent99/Tutor product names, support names, stack choices, or
  Tutor's stale security posture.
- Do not change broad reviewer invocation rules; Slice 03 owns that.
- Do not change brainstorming, `_drafts`, or review-work authority; Slice 02
  owns that.
- Do not let `local-context.md` redefine process mechanics. Temporary process
  deviations stay in `implementation/process/*`.

## Reuse Posture

- Checked: current common Required Local Layout, local process deviation files,
  local-state templates, and Agent99/Tutor process-local constraint patterns.
- Reused or extended: existing local state owns project-specific facts; existing
  process deviation files keep owning process forks; the existing Reuse Gate and
  Reviews model gains local support-order/platform-preference checks before new
  machinery is proposed.
- New machinery, if any: one required `implementation/local-context.md` file for
  product constraints that the common canon must read but must not absorb. This
  does not add a parallel approval path; it constrains existing skeleton, slice,
  review, consultation, and implementation decisions.
- Compatibility: consumers can add the file during a canon upgrade without
  changing existing milestone history.

## Dependencies

- S2 skeleton sealed and committed at `6bf839e`.
- Codex CLI available for documentation review rounds.
- Claude CLI available as the different-family seal counterpart.
- The S2 temporary broad/bypass reviewer deviation remains active until Slice 03
  seals or records a different disposition.

## Expected Files

- `canon/process/README.md`
- `canon/process/codex-review.md`
- `templates/local-state/implementation/README.md`
- `templates/local-state/implementation/local-context.md`
- `templates/local-state/implementation/milestones/_milestone/README.md`
- `templates/local-state/implementation/milestones/_milestone/slices/01-slice.md`
- `implementation/README.md`
- `implementation/local-context.md`
- `implementation/milestones/agent99-tutor-process-consolidation/**`

## Acceptance Criteria

- Required Local Layout includes `implementation/local-context.md`.
- The canon defines local context as local constraints, not process authority.
- The canon states that temporary process deviations still live in
  `implementation/process/README.md` or
  `implementation/process/codex-review.md`.
- The canon requires milestone skeletons, slice notes, consultations, and
  implementation decisions to apply any local support-order or
  platform-preference constraints before proposing new machinery.
- The canon requires reviews to check those local constraints when the reviewed
  artifact proposes new machinery.
- The template tree includes a concise `local-context.md` with sections for
  product constraints, support order or platform preference, verification
  commands, sensitive local exclusions, and temporary notes.
- The milestone and slice templates tell authors to check local context when
  filling Reuse Posture for new machinery.
- The template warns not to store secrets, credentials, tokens, private keys,
  raw PII, or raw sensitive operational data.
- This repository has its own local context that stays product-neutral and
  records no product support order.
- Existing local process deviation files remain the place for process forks.
- Slice 01 documentation review and double seal finish clean before any Slice 01
  expected file is changed for implementation.

## Tests

- `git diff --check`
- `rg -n "local-context.md" canon/process/README.md`
- `awk '/^implementation\//,/review-work\//' canon/process/README.md | rg -n "local-context.md"`
- `! rg -n "Agent99|Tutor|LPC|Life|Firebase" canon/process/README.md canon/process/codex-review.md templates/local-state/implementation implementation/local-context.md`
- `rg -n "codex exec --sandbox read-only" canon/process/codex-review.md`
- `rg -n "temporarily needs broader filesystem access" canon/process/codex-review.md`
- `rg -n "local context.*local constraints|local constraints.*local context" canon/process/README.md`
- `rg -n "local context.*not process authority|not process authority.*local context" canon/process/README.md`
- `rg -n "temporary process deviations.*implementation/process/README.md|implementation/process/README.md.*temporary process deviations" canon/process/README.md`
- `rg -n "implementation/process/codex-review.md" canon/process/README.md`
- `rg -n "Reuse Posture.*local context|local context.*Reuse Posture" canon/process/README.md`
- `rg -n "milestone skeletons.*slice notes.*implementation decisions" canon/process/README.md`
- `rg -n "consultations.*support order|support order.*consultations" canon/process/README.md`
- `rg -n "reviews.*local context|local context.*reviews" canon/process/README.md`
- `rg -n "new machinery" canon/process/README.md`
- `rg -n "local context.*review|review.*local context" canon/process/codex-review.md`
- `rg -n "support order|platform preference" canon/process/codex-review.md`
- `test -f templates/local-state/implementation/local-context.md`
- `test -f implementation/local-context.md`
- `rg -n "support order|platform preference" canon/process/README.md`
- `rg -n "^## Product Constraints" templates/local-state/implementation/local-context.md`
- `rg -n "^## Support Order Or Platform Preference" templates/local-state/implementation/local-context.md`
- `rg -n "^## Verification Commands" templates/local-state/implementation/local-context.md`
- `rg -n "^## Sensitive Local Exclusions" templates/local-state/implementation/local-context.md`
- `rg -n "^## Temporary Notes" templates/local-state/implementation/local-context.md`
- `rg -n "Do not store secrets, credentials, tokens, private keys, raw PII, or raw sensitive operational data" templates/local-state/implementation/local-context.md`
- `rg -n "process deviations" templates/local-state/implementation/local-context.md`
- `rg -n "Local context" templates/local-state/implementation/README.md`
- `rg -n "local-context.md" templates/local-state/implementation/milestones/_milestone/README.md`
- `rg -n "local-context.md" templates/local-state/implementation/milestones/_milestone/slices/01-slice.md`
- `rg -n "local-context.md" implementation/README.md`
- `rg -n "Product-neutral canon repository" implementation/local-context.md`
- `rg -n "No product support order is recorded" implementation/local-context.md`

## Risks

- `local-context.md` could become a hidden process fork. Mitigation: the canon
  says it constrains decisions but cannot redefine process mechanics.
- Product examples could leak into the common canon. Mitigation: use generic
  support-order and platform-preference language only.
- Sensitive material could be over-collected. Mitigation: the template permits
  names of exclusions but forbids storing secret or raw sensitive values.

## Review

This slice note must seal `ready` and be committed before any Slice 01 expected
file is changed for implementation.
