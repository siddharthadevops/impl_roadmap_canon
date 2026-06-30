# Slice 01 - Review Latency Reduction Without Weaker Evidence

Status: ready

## Scope

Amend the common review canon so review prompts make local inspection explicit
and double final seals launch concurrently when that is possible without
weakening seal independence.

In scope:

- local-checkout source-of-truth guidance for review prompts.
- local search/file-reading preference for speed.
- Git's role as scope, diff, history, and ref evidence.
- concurrent double-seal launch rule.
- reason recording when concurrent launch is unavailable.
- reviewed release `v0.4.0`.
- S3 local closeout state after implementation.

## Non-Goals

- Do not remove worktree before/after invalidation.
- Do not weaken no-edit, egress, local exclusion, or usable-output rules.
- Do not require a specific local search command beyond examples already common
  to the environment.
- Do not make remote Git hosting the source of review content when a local
  checkout is available.
- Do not change mandatory Codex plus Claude CLI seal pairing.

## Reuse Posture

- Checked: current `Prompt Shape`, `Worktree Check`, `Watchdog`, `Seal
  Independence`, `Double Seal`, local context, and README pinning.
- Reused or extended: no-edit review prompts, local-context exclusions,
  worktree checks, unchanged-artifact seals, same-prompt/no-peek seal rules,
  and review-log evidence.
- New machinery, if any: no tooling; only review prompt guidance and seal
  scheduling rules.
- Compatibility: existing consumers can keep the same review output and
  worktree-check format. Runners that cannot launch concurrently remain valid
  if they record the reason and preserve no-peek isolation.
- Local context: this product-neutral canon repo records no support order and
  no sensitive local exclusions; implementation must keep the rule
  product-neutral.

## Dependencies

- S3 skeleton sealed and committed at `0136881`.
- Codex CLI available for review and one seal half.
- Claude CLI available for the non-Codex seal half.

## Expected Files

- `canon/process/README.md`
- `canon/process/codex-review.md`
- `README.md`
- `VERSION`
- `implementation/roadmap.md`
- `implementation/milestones/README.md`
- `implementation/milestones/review-efficiency-and-concurrent-seals/README.md`
- `implementation/milestones/review-efficiency-and-concurrent-seals/review-log.md`
- `implementation/milestones/review-efficiency-and-concurrent-seals/slices/README.md`
- `implementation/milestones/review-efficiency-and-concurrent-seals/slices/01-review-latency-reduction.md`
- `implementation/milestones/review-efficiency-and-concurrent-seals/closures/README.md`
- `implementation/milestones/review-efficiency-and-concurrent-seals/closures/01-review-latency-reduction.md`

## Acceptance Criteria

- `codex-review.md` tells review prompts to treat the local filesystem checkout
  as the source of truth for reading reviewed content when the checkout is
  available.
- `codex-review.md` tells review prompts to prefer local search and file-reading
  tools for content inspection speed.
- `codex-review.md` says Git is used to identify reviewed scope, compare
  changes, inspect relevant history, and verify commits or refs.
- The canon does not tell reviewers to fetch remote hosting content when the
  local checkout has the content needed for review.
- The existing no-edit prompt requirement remains mandatory for broad review
  runs.
- Existing egress and Sensitive Local Exclusions rules remain mandatory.
- The existing worktree before/after invalidation remains mandatory for broad
  Codex and Claude review runs.
- Codex remains the mandatory Codex seal half, and Claude CLI remains the
  required non-Codex seal half when Codex is the worker/orchestrator.
- Existing seal usable-output rules remain mandatory: `EXIT=0`, `VERDICT:`,
  finding-count consistency, no worktree invalidation marker, and unchanged
  artifact.
- The double final seal rule says both seal halves should launch concurrently
  when both required reviewers are available and the runner can preserve
  no-peek independence.
- Concurrent seal launch still uses the same prompt and same unchanged artifact
  for both reviewers.
- If a seal cannot launch concurrently, the review log records why.
- Sequential fallback still forbids either reviewer from seeing the other's
  output before both complete.
- S3 closes as reviewed release `v0.4.0`; `VERSION`, README pinning, roadmap,
  global milestone index, S3 work log, S3 review log, and Slice 01 closure all
  reflect that state.
- Common canon wording remains product-neutral and does not add product, stack,
  support-order, or local team names.
- Slice 01 closure records the reviewed content commit and planned reviewed tag
  `v0.4.0`.
- The final release commit after the reviewed content commit contains only
  closure/bookkeeping changes.
- The reviewed tag `v0.4.0` is created on the final release commit and pushed
  with `main`.

## Release Sequence

1. Commit the sealed Slice 01 note, then commit bookkeeping that marks Slice 01
   documentation `ready`.
2. Apply canon, README pinning, `VERSION`, and roadmap changes; commit the
   reviewed content commit.
3. Run implementation review and double final seal on that content commit.
4. Add closure/bookkeeping updates recording the reviewed content commit and
   planned tag; commit the final release commit.
5. Create annotated tag `v0.4.0` on the final release commit.
6. Push `main` and `v0.4.0`.

## Pre-Tag Tests

- `git diff --check`
- `test "$(cat VERSION)" = "0.4.0"`
- `rg -n "checkout v0.4.0" README.md`
- `! rg -n "checkout v0.3.0" README.md`
- `rg -n "local filesystem checkout|local checkout" canon/process/codex-review.md`
- `rg -n "source of truth.*content|content.*source of truth" canon/process/codex-review.md`
- `rg -n "local search|file-reading|file reading" canon/process/codex-review.md`
- `rg -n "Git.*scope|scope.*Git" canon/process/codex-review.md`
- `rg -n "Git.*diff|diff.*Git|compare changes" canon/process/codex-review.md`
- `rg -n "Git.*history|history.*Git" canon/process/codex-review.md`
- `rg -n "Git.*refs|refs.*Git|commits.*refs|refs.*commits" canon/process/codex-review.md`
- `! rg -n "GitHub.*source of truth|remote.*source of truth|fetch.*review content" canon/process/codex-review.md`
- `rg -n "must not edit|must not.*modify|review-only" canon/process/codex-review.md`
- `rg -n "Sensitive Local Exclusions|sensitive local exclusions" canon/process/codex-review.md`
- `rg -n "Never send secrets|raw sensitive operational data|egress" canon/process/codex-review.md`
- `rg -n "worktree.*before.*after|before.*after.*worktree" canon/process/codex-review.md`
- `rg -n "INVALID: worktree changed|worktree changed.*invalid" canon/process/codex-review.md`
- `rg -n "Codex.*mandatory Codex seal half|mandatory Codex seal half|Codex remains.*seal half" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Claude CLI.*required non-Codex|required non-Codex.*Claude CLI|non-Codex.*Claude CLI" canon/process/README.md canon/process/codex-review.md`
- `rg -n "Codex seal:.*EXIT=0.*VERDICT|Codex seal.*finding-count|Codex seal.*unchanged artifact" canon/process/codex-review.md`
- `rg -n "Claude CLI seal:.*EXIT=0.*VERDICT|Claude CLI seal.*finding-count|Claude CLI seal.*unchanged artifact" canon/process/codex-review.md`
- `rg -n "concurrent|concurrently" canon/process/README.md canon/process/codex-review.md`
- `rg -n "same prompt|same review prompt" canon/process/README.md canon/process/codex-review.md`
- `rg -n "same unchanged artifact|unchanged artifact" canon/process/README.md canon/process/codex-review.md`
- `rg -n "no-peek|other.*output|output.*other" canon/process/README.md canon/process/codex-review.md`
- `rg -n "record.*reason|reason.*record" canon/process/README.md canon/process/codex-review.md`
- `rg -n "not.*concurrent|cannot.*concurrent|unable.*concurrent|sequential" canon/process/README.md canon/process/codex-review.md`
- `rg -n "S3.*review latency|review latency.*S3" implementation/roadmap.md`
- `rg -n "reviewed release.*v0.4.0|v0.4.0.*reviewed release" implementation/roadmap.md`
- `! rg -n "Agent99|Tutor|LPC|Life|Firebase|Phoenix|Elixir|Siddhartha" canon/process/README.md canon/process/codex-review.md`
- `rg -n "\\| S3 \\| Review efficiency and concurrent seals \\| Process canon \\| Closed \\(reviewed release \`v0.4.0\`\\)" implementation/milestones/README.md`
- `awk '/^## Active Continuation/{p=1; next} /^## /{p=0} p' implementation/milestones/README.md | rg -n "No active milestone|future canon change"`
- `! awk '/^## Active Continuation/{p=1; next} /^## /{p=0} p' implementation/milestones/README.md | rg -n "S3|review-efficiency-and-concurrent-seals|current unit|Slice 01"`
- `rg -n "^Status: closed$" implementation/milestones/review-efficiency-and-concurrent-seals/README.md`
- `rg -n "\\| 01 \\| Review latency reduction without weaker evidence \\| closed \\|" implementation/milestones/review-efficiency-and-concurrent-seals/README.md`
- `awk '/^## Current Slice/{p=1; next} /^## /{p=0} p' implementation/milestones/review-efficiency-and-concurrent-seals/README.md | rg -n "None|closed"`
- `awk '/^## Continuation/{p=1; next} /^## /{p=0} p' implementation/milestones/review-efficiency-and-concurrent-seals/README.md | rg -n "closed|global milestone index|roadmap"`
- `rg -n "## Slice 01 Documentation" implementation/milestones/review-efficiency-and-concurrent-seals/review-log.md`
- `rg -n "## Slice 01 Implementation" implementation/milestones/review-efficiency-and-concurrent-seals/review-log.md`
- `rg -n "slice-01-impl-seal" implementation/milestones/review-efficiency-and-concurrent-seals/review-log.md`
- `test -f implementation/milestones/review-efficiency-and-concurrent-seals/closures/01-review-latency-reduction.md`
- `rg -n "01-review-latency-reduction.md|Slice 01 - Review Latency Reduction" implementation/milestones/review-efficiency-and-concurrent-seals/closures/README.md`
- `rg -n "Status: closed" implementation/milestones/review-efficiency-and-concurrent-seals/closures/01-review-latency-reduction.md`
- `rg -n "Review state:.*review_clean|review_clean.*Review state" implementation/milestones/review-efficiency-and-concurrent-seals/closures/01-review-latency-reduction.md`
- `rg -n "Planned reviewed tag: \`v0.4.0\`" implementation/milestones/review-efficiency-and-concurrent-seals/closures/01-review-latency-reduction.md`
- `reviewed_commit=$(awk -F'\`' '/Reviewed content commit/{print $2; exit}' implementation/milestones/review-efficiency-and-concurrent-seals/closures/01-review-latency-reduction.md); test -n "$reviewed_commit" && git cat-file -e "$reviewed_commit^{commit}" && test -z "$(git diff --name-only "$reviewed_commit"..HEAD | rg -v '^(implementation/milestones/README.md|implementation/milestones/review-efficiency-and-concurrent-seals/README.md|implementation/milestones/review-efficiency-and-concurrent-seals/review-log.md|implementation/milestones/review-efficiency-and-concurrent-seals/closures/README.md|implementation/milestones/review-efficiency-and-concurrent-seals/closures/01-review-latency-reduction.md)$')"`

## Post-Tag Tests

- `test "$(git rev-list -n 1 v0.4.0)" = "$(git rev-parse HEAD)"`
- `test "$(git show v0.4.0:VERSION)" = "0.4.0"`
- `git rev-parse "v0.4.0^{tag}"`
- `test "$(git ls-remote origin refs/heads/main | awk '{print $1}')" = "$(git rev-parse HEAD)"`
- `test "$(git ls-remote origin refs/tags/v0.4.0 | awk '{print $1}')" = "$(git rev-parse "v0.4.0^{tag}")"`
- `test "$(git ls-remote origin 'refs/tags/v0.4.0^{}' | awk '{print $1}')" = "$(git rev-list -n 1 v0.4.0)"`

## Risks

- The local-checkout rule could be misread as forbidding Git evidence.
  Mitigation: Git's scope, diff, history, and ref role is explicit.
- Concurrent seal launch could accidentally share outputs. Mitigation:
  concurrent launch is allowed only when no-peek independence is preserved.
- Tooling may be unable to launch both halves at the same time. Mitigation:
  record the reason and preserve no-peek sequential isolation.

## Review

This slice note must seal `ready` and be committed before common canon files are
changed for implementation.
