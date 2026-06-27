# Agent99/Tutor Process Consolidation

Status: open (Slice 02 documentation)

## Boundary

Move the reusable process rules proven in Agent99 and Tutor into the common
canon so consuming projects keep only local context, live state, and explicit
temporary deviations.

## Non-Goals

- Do not canonize Agent99/Tutor product names, support names, stack choices, or
  stale local security posture.
- Do not reopen closed S0/S1 outcomes or redesign release tagging.
- Do not add automation or new runner tooling in the skeleton.
- Do not let local context redefine the common process except through explicit
  temporary deviations.

## Canonical Basis

- Common process: [`../../../canon/process/README.md`](../../../canon/process/README.md)
- Review runner: [`../../../canon/process/codex-review.md`](../../../canon/process/codex-review.md)
- Local review deviation register: [`../../process/codex-review.md`](../../process/codex-review.md)
- Agent99 process references:
  `/Users/siddhartha/Development/source/life_prod/agent_99/implementation/process/README.md`
  and
  `/Users/siddhartha/Development/source/life_prod/agent_99/implementation/process/codex-review.md`
- Tutor process references:
  `/Users/siddhartha/Development/source/life_prod/tutor/implementation/process/README.md`
  and
  `/Users/siddhartha/Development/source/life_prod/tutor/implementation/process/codex-review.md`
- Prior reviewed release: `v0.2.0`
- Operator direction: for S2 review runs, use broad/bypass reviewer invocation
  as a temporary local deviation while the common invocation rule is under
  review; prompts must still say not to edit, and worktree snapshots must prove
  the run made no changes. Broad review access is relevance-driven: inspect the
  S2 artifact, its canonical references, and related Agent99/Tutor process
  context, but do not inspect unrelated personal material, secrets, credentials,
  tokens, private keys, or raw sensitive product data.
- Operator correction: Tutor's current read-only/security posture is stale and
  must not drive the common access default; use Tutor for process shape and
  reviewer-independence lessons only.

## Reuse Posture

- Checked: Agent99 and Tutor process docs, brainstorming/draft layout, review
  runner rules, and local process adaptations. Review logs were used only as
  pointers to prior failure modes and relevant process text, not as authority.
- Reused or extended: the existing common milestone/slice/review/seal model,
  S1 cross-model adjudication, local-state templates, and review evidence
  capture.
- New machinery, if any: one required local context file, common rules for
  non-canonical planning material, broad reviewer invocation defaults, and seal
  reviewer independence/fallback/usable-output evidence rules.
  Existing process/deviation files say how a repo differs from the canon; the
  new file records product constraints the common canon must read without
  turning them into process forks. Broad invocation extends the existing
  `codex-review.md` deviation path into a reviewed common rule, while retaining
  no-edit, worktree snapshot, egress, and local-context constraints. S2's target
  common default is broad tool-enabled review for Codex and Claude;
  `local-context.md` can name explicit exclusions and sensitive-data
  boundaries. Until Slice 03 seals, broad invocation remains an
  operator-authorized S2-local deviation from the current `v0.2.0` read-only
  baseline. Until each planned slice seals, its corresponding rule is an S2
  target rather than active common canon.
- Compatibility: existing consumers can adopt the new layout incrementally; any
  local fork remains a recorded local deviation until removed.

## Shared Contract

This is the target contract S2 must make canonical slice by slice. The common
canon owns process mechanics. Each consuming project owns local constraints in
local state. Slice 01 must add required local context and support-order
constraints. Slice 02 must add the non-canonical material rules: brainstorming
is durable exploration, `_drafts` holds cleaner implementation guides, a sealed
milestone or slice can convert relevant guide decisions or operator-named
planning material into implementation authority only through explicit Adopt /
Revise / Reject decisions, and review scratch is mechanical evidence only.

When local context defines a support order or platform preference, reviews and
consultations must enforce it whenever new machinery is proposed, without
hard-coding any one product's support names into the common canon. Slice 03 must
make the target common review invocation broad bypass/tool-enabled inspection
for Codex and Claude, while local context supplies explicit exclusions, such as
secrets or files not to read, and those exclusions win. Slice 04 must add seal
reviewer independence, fallback handling, and usable-output evidence rules.
Until the relevant slice seals, each statement remains an S2 target rather than
current common canon.

## Slices

| Slice | Title | Status | Notes |
|---|---|---|---|
| 01 | Local context and support order | closed | Add required local context to Required Local Layout and define local support-order constraints. |
| 02 | Non-canonical planning material | planned | Add brainstorming, `_drafts` implementation guides, review-work, and Adopt / Revise / Reject rules. |
| 03 | Broad reviewer invocation | planned | Add bypass reviewer commands, no-edit guardrails, egress boundaries, and worktree checks. |
| 04 | Seal reviewer independence | planned | Add independent seal reviewer selection, fallback handling, and usable-output evidence rules. |

## Work Log

| Order | Unit | Phase | Status | Review | Commit | Notes |
|---|---|---|---|---|---|---|
| 01 | Skeleton | doc | ready | skeleton-doc-r26 + seal-a11 | 6bf839e | Double seal clean; no accepted debt. |
| 02 | Slice 01 | doc | ready | slice-01-doc-r12 + seal-a3 | 3a058d1 | Double seal clean; no accepted debt. |
| 03 | Slice 01 | impl | review_clean | slice-01-impl-r2 + seal-a2 | 5039353 | Fixed seal-a1 P3 clarity finding; no accepted debt. |
| 04 | Slice 01 | closure | closed | | | Closure/bookkeeping recorded. |

## Current Slice

Slice 02 documentation.

## Continuation

Draft Slice 02 documentation for non-canonical planning material. For S2 only,
use the operator-authorized broad reviewer invocation deviation with explicit
no-edit prompt text, relevance-driven egress boundaries, and before/after
worktree checks.
