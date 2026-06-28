# Agent99/Tutor Process Consolidation

Status: open (Slice 04 implementation)

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
| 02 | Non-canonical planning material | closed | Add brainstorming, `_drafts` implementation guides, review-work, and Adopt / Revise / Reject rules. |
| 03 | Broad reviewer invocation | closed | Add bypass reviewer commands, no-edit guardrails, egress boundaries, and worktree checks. |
| 04 | Seal reviewer independence | ready | Add independent seal reviewer selection, fallback handling, and usable-output evidence rules. |

## Work Log

| Order | Unit | Phase | Status | Review | Commit | Notes |
|---|---|---|---|---|---|---|
| 01 | Skeleton | doc | ready | skeleton-doc-r26 + seal-a11 | 6bf839e | Double seal clean; no accepted debt. |
| 02 | Slice 01 | doc | ready | slice-01-doc-r12 + seal-a3 | 3a058d1 | Double seal clean; no accepted debt. |
| 03 | Slice 01 | impl | review_clean | slice-01-impl-r2 + seal-a2 | 5039353 | Fixed seal-a1 P3 clarity finding; no accepted debt. |
| 04 | Slice 01 | closure | closed | | | Closure/bookkeeping recorded. |
| 05 | Slice 02 | doc | findings | slice-02-doc-r1 | | 2 P2 findings; both valid. |
| 06 | Slice 02 | doc | fixed | slice-02-doc-r1 | | Added template Adopt/Revise/Reject coverage and codex-review review-work tests; fresh review due. |
| 07 | Slice 02 | doc | findings | slice-02-doc-r2 | | 2 P2 findings; both valid. |
| 08 | Slice 02 | doc | fixed | slice-02-doc-r2 | | Expanded product-neutrality and prompt-shape tests; fresh review due. |
| 09 | Slice 02 | doc | findings | slice-02-doc-r3 | | 1 P2 finding; valid. |
| 10 | Slice 02 | doc | fixed | slice-02-doc-r3 | | Added `_drafts` process-doc boundary test; fresh review due. |
| 11 | Slice 02 | doc | findings | slice-02-doc-r4 | | 3 P2 findings; all valid. |
| 12 | Slice 02 | doc | fixed | slice-02-doc-r4 | | Added Required Local Layout and process-doc boundary tests. |
| 13 | Slice 02 | doc | review_requested | slice-02-doc-r5 | | Fresh review launched after r4 fixes. |
| 14 | Slice 02 | doc | findings | slice-02-doc-r5 | | 1 P2 finding; valid. |
| 15 | Slice 02 | doc | fixed | slice-02-doc-r5 | | Tightened `_drafts` non-canonical-context prompt-shape test. |
| 16 | Slice 02 | doc | review_requested | slice-02-doc-r6 | | Fresh review launched after r5 fix. |
| 17 | Slice 02 | doc | findings | slice-02-doc-r6 | | 2 P2 findings; both valid. |
| 18 | Slice 02 | doc | fixed | slice-02-doc-r6 | | Added may-remain-empty and layout-role tests. |
| 19 | Slice 02 | doc | review_requested | slice-02-doc-r7 | | Fresh review launched after r6 fixes. |
| 20 | Slice 02 | doc | review_requested | slice-02-doc-r7 + seal-a1 | | Codex r7 clean; documentation double seal launched. |
| 21 | Slice 02 | doc | ready | slice-02-doc-r7 + seal-a1 | f75a1fd | Double seal clean; no accepted debt. |
| 22 | Slice 02 | impl | verified | | 70310be | Full Slice 02 test list passed. |
| 23 | Slice 02 | impl | review_clean | slice-02-impl-r1 + seal-a1 | 70310be | Codex review and double seal clean; no accepted debt. |
| 24 | Slice 02 | closure | closed | | | Closure/bookkeeping recorded. |
| 25 | Slice 03 | doc | review_requested | slice-03-doc-r1 | | Drafted broad reviewer invocation slice note. |
| 26 | Slice 03 | doc | findings | slice-03-doc-seal-a1 | | Seal broke with one Codex P2, one Claude P1, and one Claude P3; all valid. |
| 27 | Slice 03 | doc | fixed | slice-03-doc-seal-a1 | | Added stale-deviation, untracked-hash, and never-send clarification tests. |
| 28 | Slice 03 | doc | review_requested | slice-03-doc-r2 | | Fresh review launched after seal-a1 fixes. |
| 29 | Slice 03 | doc | findings | slice-03-doc-seal-a2 | | Seal broke with one Codex P1 and one Claude P3; both valid. |
| 30 | Slice 03 | doc | fixed | slice-03-doc-seal-a2 | | Fixed continuation and traced the reusable egress floor. |
| 31 | Slice 03 | doc | review_requested | slice-03-doc-r3 | | Fresh review launched after seal-a2 fixes. |
| 32 | Slice 03 | doc | findings | slice-03-doc-r3 | | Codex found two P2 test-strength gaps; both valid. |
| 33 | Slice 03 | doc | fixed | slice-03-doc-r3 | | Split never-send category tests and broadened the Slice 04 guard. |
| 34 | Slice 03 | doc | review_requested | slice-03-doc-r4 | | Fresh review due after r3 fixes. |
| 35 | Slice 03 | doc | findings | slice-03-doc-r4 | | Codex found one P1 and one P2; both valid. |
| 36 | Slice 03 | doc | fixed | slice-03-doc-r4 | | Blocked seal-selection bleed-through and required continuation cleanup after implementation. |
| 37 | Slice 03 | doc | review_requested | slice-03-doc-r5 | | Fresh review due after r4 fixes. |
| 38 | Slice 03 | doc | findings | slice-03-doc-r5 | | Codex found two P2 readiness gaps; both valid. |
| 39 | Slice 03 | doc | fixed | slice-03-doc-r5 | | Added the global milestone index and fuller egress tests. |
| 40 | Slice 03 | doc | review_requested | slice-03-doc-r6 | | Fresh review due after r5 fixes. |
| 41 | Slice 03 | doc | findings | slice-03-doc-r6 | | Codex found two P2 guardrail gaps; both valid. |
| 42 | Slice 03 | doc | fixed | slice-03-doc-r6 | | Added Claude worktree test coverage and narrowed expected local milestone files. |
| 43 | Slice 03 | doc | review_requested | slice-03-doc-r7 | | Fresh review due after r6 fixes. |
| 44 | Slice 03 | doc | findings | slice-03-doc-r7 | | Codex found one P2 stale-local-state gap; valid. |
| 45 | Slice 03 | doc | fixed | slice-03-doc-r7 | | Required the milestone README to stop describing broad invocation as a temporary S2-local deviation after implementation. |
| 46 | Slice 03 | doc | review_requested | slice-03-doc-r8 | | Fresh review due after r7 fix. |
| 47 | Slice 03 | doc | findings | slice-03-doc-r8 | | Codex found one P1 Slice 04 boundary leak; valid. |
| 48 | Slice 03 | doc | fixed | slice-03-doc-r8 | | Reworded Claude dependency without seal-counterpart semantics. |
| 49 | Slice 03 | doc | review_requested | slice-03-doc-r9 | | Fresh review due after r8 fix. |
| 50 | Slice 03 | doc | findings | slice-03-doc-r9 | | Codex found two P2 test gaps; both valid. |
| 51 | Slice 03 | doc | fixed | slice-03-doc-r9 | | Added complete no-edit and Claude/review-CLI egress test coverage. |
| 52 | Slice 03 | doc | review_requested | slice-03-doc-r10 | | Fresh review due after r9 fixes. |
| 53 | Slice 03 | doc | review_requested | slice-03-doc-r10 + seal-a3 | | Codex r10 clean; documentation double seal launched. |
| 54 | Slice 03 | doc | findings | slice-03-doc-seal-a3 | | Seal broke with three Claude findings; all valid. |
| 55 | Slice 03 | doc | fixed | slice-03-doc-seal-a3 | | Limited stale-deviation cleanup to active state, added local-deviation precedence test, and fixed continuation cleanup coverage. |
| 56 | Slice 03 | doc | review_requested | slice-03-doc-r11 | | Fresh review due after seal-a3 fixes. |
| 57 | Slice 03 | doc | review_requested | slice-03-doc-r11 + seal-a4 | | Codex r11 clean; documentation double seal launched. |
| 58 | Slice 03 | doc | findings | slice-03-doc-seal-a4 | | Seal broke with one Claude P2; valid. |
| 59 | Slice 03 | doc | fixed | slice-03-doc-seal-a4 | | Split redacted-excerpt egress coverage into its own test. |
| 60 | Slice 03 | doc | review_requested | slice-03-doc-r12 | | Fresh review due after seal-a4 fix. |
| 61 | Slice 03 | doc | review_requested | slice-03-doc-r12 + seal-a5 | | Codex r12 clean; documentation double seal launched. |
| 62 | Slice 03 | doc | findings | slice-03-doc-seal-a5 | | Seal broke with one rejected Codex P1 and one valid Claude P2. |
| 63 | Slice 03 | doc | fixed | slice-03-doc-seal-a5 | | Strengthened active-continuation cleanup coverage against line wrapping. |
| 64 | Slice 03 | doc | review_requested | slice-03-doc-r13 | | Fresh review due after seal-a5 fix. |
| 65 | Slice 03 | doc | findings | slice-03-doc-r13 | | Codex found one P2 multiline cleanup gap; valid. |
| 66 | Slice 03 | doc | fixed | slice-03-doc-r13 | | Switched active-state cleanup test to multiline whitespace matching and aligned milestone status. |
| 67 | Slice 03 | doc | review_requested | slice-03-doc-r14 | | Fresh review due after r13 fix. |
| 68 | Slice 03 | doc | review_requested | slice-03-doc-r14 + seal-a6 | | Codex r14 clean; documentation double seal launched. |
| 69 | Slice 03 | doc | ready | slice-03-doc-r14 + seal-a6 | | Double seal clean; no accepted debt. |
| 70 | Slice 03 | impl | verified | | 5c77118 | Full Slice 03 test list passed. |
| 71 | Slice 03 | impl | findings | slice-03-impl-r1 + seal-a1 | | Rejected one stale-history finding after Claude consultation; fixed one valid Claude P3 wrap finding. |
| 72 | Slice 03 | impl | review_clean | slice-03-impl-r2 + seal-a2 | 5c77118 | Codex review and double seal clean; no accepted debt. |
| 73 | Slice 03 | closure | closed | | | Closure/bookkeeping recorded. |
| 74 | Slice 04 | doc | review_requested | slice-04-doc-r1 | | Drafted seal reviewer independence slice note. |
| 75 | Slice 04 | doc | fixed | slice-04-doc-r1 | | Added exact global Active Continuation closeout tests. |
| 76 | Slice 04 | doc | fixed | slice-04-doc-r2 | | Required authorized fallback seal output to meet usable-evidence rules. |
| 77 | Slice 04 | doc | fixed | slice-04-doc-seal-a1 | | Added same-prompt seal isolation, roadmap closeout, and Claude 30-minute watchdog scope tests. |
| 78 | Slice 04 | doc | fixed | slice-04-doc-seal-a2 | | Added Slice 04 closure and Claude `EXIT=` record-field coverage. |
| 79 | Slice 04 | doc | fixed | slice-04-doc-r5 | | Added exact global S2 closed-row and review-log closeout tests. |
| 80 | Slice 04 | doc | fixed | slice-04-doc-r6 | | Added closure index closeout coverage. |
| 81 | Slice 04 | doc | fixed | slice-04-doc-r7 | | Added reviewed release `v0.3.0` and Tutor read-only wording guards. |
| 82 | Slice 04 | doc | fixed | slice-04-doc-r8 | | Added Codex seal usable-output and post-seal release-commit scope checks. |
| 83 | Slice 04 | doc | review_requested | slice-04-doc-r10 | | Fresh review due after r9 fixes. |
| 84 | Slice 04 | doc | fixed | slice-04-doc-r10 | | Added Claude-specific usable-output tests and corrected review-requested provenance. |
| 85 | Slice 04 | doc | review_requested | slice-04-doc-r11 | | Fresh review due after r10 fixes. |
| 86 | Slice 04 | doc | fixed | slice-04-doc-r11 | | Added explicit milestone status/current-slice/continuation closeout tests. |
| 87 | Slice 04 | doc | review_requested | slice-04-doc-r12 | | Fresh review due after r11 fix. |
| 88 | Slice 04 | doc | fixed | slice-04-doc-seal-a3 | | Split fallback independence tests, clarified watchdog scope, and required reviewed-release index status. |
| 89 | Slice 04 | doc | fixed | slice-04-doc-seal-a4 | | Narrowed Claude watchdog guard and added Slice 04 closure work-log coverage. |
| 90 | Slice 04 | doc | review_requested | slice-04-doc-r14 | | Fresh review due after seal-a4 fixes. |
| 91 | Slice 04 | doc | fixed | slice-04-doc-r14 | | Added missing review-requested provenance for r14. |
| 92 | Slice 04 | doc | review_requested | slice-04-doc-r15 | | Fresh review due after r14 fix. |
| 93 | Slice 04 | doc | fixed | slice-04-doc-r15 | | Split required record-field and restricted-mode tests. |
| 94 | Slice 04 | doc | review_requested | slice-04-doc-r16 | | Fresh review due after r15 fix. |
| 95 | Slice 04 | doc | fixed | slice-04-doc-r16 | | Tied Claude/fallback usable-output tests to their specific seal outputs. |
| 96 | Slice 04 | doc | review_requested | slice-04-doc-r17 | | Fresh review due after r16 fixes. |
| 97 | Slice 04 | doc | fixed | slice-04-doc-seal-a5 | | Split fallback forbidden-replacement tests and recorded Slice 04 documentation review-log traceability. |
| 98 | Slice 04 | doc | review_requested | slice-04-doc-r18 | | Fresh review due after seal-a5 fixes. |
| 99 | Slice 04 | doc | fixed | slice-04-doc-seal-a6 | | Scoped active-state closeout tests and added seal-specific worktree/unchanged-artifact checks. |
| 100 | Slice 04 | doc | review_requested | slice-04-doc-r19 | | Fresh review due after seal-a6 fixes. |
| 101 | Slice 04 | doc | fixed | slice-04-doc-seal-a7 | | Updated review-log traceability through a7 and tightened restricted-mode tests. |
| 102 | Slice 04 | doc | review_requested | slice-04-doc-r20 | | Fresh review due after seal-a7 fixes. |
| 103 | Slice 04 | doc | ready | slice-04-doc-r20 + seal-a8 | | Double seal clean; no accepted debt. |

## Current Slice

Slice 04 implementation.

## Continuation

Implement Slice 04 from the sealed slice note, then run implementation review.
