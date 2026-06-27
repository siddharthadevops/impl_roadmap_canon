# Slice 02 - Non-Canonical Planning Material

Status: ready

## Scope

Move the Agent99-proven planning-material rules into the common canon:
`implementation/brainstorming/`, `implementation/_drafts/`, and
`implementation/review-work/` must have distinct authority boundaries.

In scope:

- common process language for brainstorming, `_drafts`, review-work, and
  Adopt / Revise / Reject.
- common review prompt language for non-canonical planning context.
- local-state template READMEs for brainstorming and `_drafts`.
- this repository's own empty planning-material READMEs.
- S2 local state and review records.

## Non-Goals

- Do not review or canonize product or architecture content from Agent99 or
  Tutor brainstorming.
- Do not add product examples, support names, stack choices, or stale local
  access posture to the common canon.
- Do not change broad reviewer invocation rules; Slice 03 owns that.
- Do not change seal reviewer independence or fallback handling; Slice 04 owns
  that.
- Do not require every consumer to keep active brainstorming or draft content.

## Reuse Posture

- Checked: Agent99 process rules for brainstorming, `_drafts`, review-work, and
  process-doc review scope; current common Required Local Layout and review
  prompt shape; local-state template structure.
- Reused or extended: existing common authority split, Reuse Gate,
  review-work scratch model, and documentation discipline.
- New machinery, if any: two local-state planning directories with README files
  and common rules for how non-canonical material can become authority.
- Compatibility: consumers without planning material can keep the directories
  empty; existing review-work scratch remains ignored and regenerable.
- Local context: no product support order is recorded for this repository.

## Dependencies

- S2 Slice 01 closed at `16fa249`.
- Codex CLI available for documentation review rounds.
- Claude CLI available as the different-family seal counterpart.
- The S2 temporary broad/bypass reviewer deviation remains active until Slice 03
  seals or records a different disposition.

## Expected Files

- `canon/process/README.md`
- `canon/process/codex-review.md`
- `templates/local-state/implementation/README.md`
- `templates/local-state/implementation/brainstorming/README.md`
- `templates/local-state/implementation/_drafts/README.md`
- `templates/local-state/implementation/milestones/_milestone/README.md`
- `templates/local-state/implementation/milestones/_milestone/slices/01-slice.md`
- `implementation/README.md`
- `implementation/brainstorming/README.md`
- `implementation/_drafts/README.md`
- `implementation/milestones/agent99-tutor-process-consolidation/**`

## Acceptance Criteria

- The canon defines `implementation/brainstorming/` as tracked exploratory
  product or architecture thinking that is non-canonical, not implementation
  authority, and not a canonical dependency.
- The canon defines `implementation/_drafts/` as non-canonical
  implementation-intent guides that may record direction, sequencing, and risks
  but do not authorize implementation or override sealed artifacts.
- The common Required Local Layout lists `implementation/brainstorming/` and
  `implementation/_drafts/` with their non-canonical roles.
- The canon defines `implementation/review-work/` as git-ignored mechanical
  review scratch for prompts, findings, seals, adjudications, and process-gate
  consultation outputs, not durable architecture or guide material.
- A milestone or slice may use brainstorming or `_drafts` only as
  non-canonical planning context unless its own reviewed artifact explicitly
  Adopts / Revises / Rejects the relevant decisions.
- Process-doc reviews cover the planning-material mechanism and link wording,
  not product or architecture content inside brainstorming or `_drafts`, unless
  the operator explicitly names that content as the review artifact.
- Review prompt shape tells reviewers to treat named brainstorming and `_drafts`
  as non-canonical context and to check Adopt / Revise / Reject instead of
  approving the linked material.
- Milestone and slice templates give authors a standard place to name any
  non-canonical planning material and Adopt / Revise / Reject relevant
  decisions.
- The review runner states that review-work must not hold durable architecture
  or guide material.
- Local-state templates include concise README files for brainstorming and
  `_drafts`.
- This repository includes product-neutral empty README files for its own
  brainstorming and `_drafts` directories.
- The planning-material README files state that those directories may remain
  empty when a consumer has no active planning material.
- The common canon and templates remain product-neutral.

## Tests

- `git diff --check`
- `rg -n "brainstorming" canon/process/README.md`
- `rg -n "_drafts" canon/process/README.md`
- `awk '/^## Required Local Layout/{p=1; next} /^## /{p=0} p' canon/process/README.md | rg "brainstorming/"`
- `awk '/^## Required Local Layout/{p=1; next} /^## /{p=0} p' canon/process/README.md | rg "_drafts/"`
- `awk '/^## Required Local Layout/{p=1; next} /^## /{p=0} p' canon/process/README.md | rg "brainstorming/.*non-canonical|non-canonical.*brainstorming/"`
- `awk '/^## Required Local Layout/{p=1; next} /^## /{p=0} p' canon/process/README.md | rg "_drafts/.*non-canonical|non-canonical.*_drafts/"`
- `rg -n "review-work.*mechanical review|mechanical review.*review-work" canon/process/README.md`
- `rg -n "brainstorming.*non-canonical|non-canonical.*brainstorming" canon/process/README.md`
- `rg -n "_drafts.*non-canonical|non-canonical.*_drafts" canon/process/README.md`
- `rg -n "Adopt / Revise / Reject" canon/process/README.md canon/process/codex-review.md`
- `rg -n "process-doc.*brainstorming|brainstorming.*process-doc" canon/process/codex-review.md`
- `rg -n "process-doc.*_drafts|_drafts.*process-doc" canon/process/codex-review.md`
- `rg -n "process-doc.*mechanism.*link|mechanism.*link.*process-doc" canon/process/codex-review.md`
- `rg -n "operator.*names.*content|content.*operator.*names" canon/process/codex-review.md`
- `rg -n "named brainstorming.*non-canonical|non-canonical.*named brainstorming" canon/process/codex-review.md`
- `rg -n "named .*_drafts.*non-canonical context|non-canonical context.*named .*_drafts" canon/process/codex-review.md`
- `rg -n "Adopt / Revise / Reject" canon/process/codex-review.md`
- `rg -n "review-work.*durable architecture|durable architecture.*review-work|review-work.*guide material|guide material.*review-work" canon/process/codex-review.md`
- `test -f templates/local-state/implementation/brainstorming/README.md`
- `test -f templates/local-state/implementation/_drafts/README.md`
- `test -f implementation/brainstorming/README.md`
- `test -f implementation/_drafts/README.md`
- `rg -n "Non-Canonical Planning" templates/local-state/implementation/milestones/_milestone/README.md`
- `rg -n "Non-Canonical Planning" templates/local-state/implementation/milestones/_milestone/slices/01-slice.md`
- `rg -n "Adopt / Revise / Reject" templates/local-state/implementation/milestones/_milestone/README.md`
- `rg -n "Adopt / Revise / Reject" templates/local-state/implementation/milestones/_milestone/slices/01-slice.md`
- `rg -n "tracked exploratory" templates/local-state/implementation/brainstorming/README.md`
- `rg -n "not canon|non-canonical" templates/local-state/implementation/brainstorming/README.md`
- `rg -n "implementation-intent guides" templates/local-state/implementation/_drafts/README.md`
- `rg -n "not canon|non-canonical" templates/local-state/implementation/_drafts/README.md`
- `rg -n "Product-neutral canon repository" implementation/brainstorming/README.md implementation/_drafts/README.md`
- `rg -n "may remain empty|can remain empty" templates/local-state/implementation/brainstorming/README.md templates/local-state/implementation/_drafts/README.md implementation/brainstorming/README.md implementation/_drafts/README.md`
- `! rg -n "Agent99|Tutor|LPC|Life|Firebase|Phoenix|Elixir" canon/process/README.md canon/process/codex-review.md templates/local-state/implementation/README.md templates/local-state/implementation/brainstorming templates/local-state/implementation/_drafts templates/local-state/implementation/milestones/_milestone/README.md templates/local-state/implementation/milestones/_milestone/slices/01-slice.md implementation/README.md implementation/brainstorming implementation/_drafts`
- `rg -n "Local planning" templates/local-state/implementation/README.md implementation/README.md`

## Risks

- Non-canonical material could look like authority. Mitigation: require explicit
  Adopt / Revise / Reject inside reviewed milestone or slice artifacts.
- Process-doc reviews could accidentally approve product designs. Mitigation:
  review the mechanism and links only unless the operator names the content.
- Empty planning directories could feel mandatory. Mitigation: README files say
  the directories may remain empty.

## Review

This slice note must seal `ready` and be committed before any Slice 02 expected
file is changed for implementation.
