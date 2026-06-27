# Slice 01 - Bootstrap Review And Reviewed Release

Status: ready

## Scope

Review the repository bootstrap as a consuming project of its own canon, fix any
review findings, and publish a reviewed release tag.

In scope:

- root repository docs and version marker.
- common canon docs under `canon/`.
- local-state templates under `templates/local-state/`.
- local implementation state under `implementation/`.
- Git history and release-tag guidance, without rewriting `v0.1.0`.

## Non-Goals

- Add generators, installers, or automation.
- Migrate Agent99 or Tutor to this canon in this slice.
- Change already-published `v0.1.0`.
- Store product-specific status in `canon/`.

## Reuse Posture

- Checked: current bootstrap docs and templates.
- Reused or extended: the existing local-state template shape is used directly
  for this repository's live `implementation/` state.
- New machinery, if any: none.
- Compatibility: any bootstrap corrections ship in a new tag so existing pins
  remain stable.

## Dependencies

- Local Git repository on `main` with clean working tree before release.
- GitHub remote `origin` at `siddharthadevops/impl_roadmap_canon`.
- Existing published tag `v0.1.0` remains immutable.
- Canon references under `canon/process/`.
- Codex CLI available for review rounds.
- A second independent seal reviewer available before closure.

## Expected Files

- `README.md`
- `VERSION`
- `canon/**`
- `templates/local-state/**`
- `implementation/**`

## Acceptance Criteria

- The repo has local state that points to the canon instead of duplicating it.
- Codex review of the slice documentation records no unresolved findings.
- The slice documentation double seal has two independent clean halves.
- The sealed slice note is committed before bootstrap implementation fixes
  begin.
- Codex review of the bootstrap content records no unresolved findings.
- The bootstrap implementation/release final seal has two independent clean
  halves.
- `VERSION` advances from `0.1.0` and matches the reviewed release tag.
- Public pinning guidance points to the reviewed tag, not `v0.1.0`.
- Closure records the reviewed content commit and the planned reviewed tag.
- The milestone review log summarizes slice documentation review, bootstrap
  review, final seals, and closure outcome.
- Milestone index, work log, and Active Continuation record S0 closed.
- The post-seal release commit contains bookkeeping/closure changes only; any
  substantive canon, template, README, or `VERSION` change reopens review.
- The reviewed tag is pushed to GitHub.

## Release Sequence

1. Commit the sealed Slice 01 note.
2. Apply bootstrap fixes and `VERSION` update, then commit the reviewed content
   commit.
3. Run bootstrap review and double final seal on that reviewed content commit.
4. Add closure/bookkeeping updates recording the reviewed content commit and
   planned reviewed tag, then commit the final release commit. This commit is
   bookkeeping only.
5. Create an annotated tag for the final release commit.
6. Push `main` and the reviewed tag to GitHub.

## Tests

- `git status -sb`
- `git log --oneline --decorate -3`
- `git ls-remote --heads --tags origin`
- `test "$(git rev-parse v0.1.0^{tag})" = "aac36f2fa3cb8d5b9e1d469a9ddb5807c91a9061"`
- `test "$(git ls-remote origin refs/tags/v0.1.0 | awk '{print $1}')" = "aac36f2fa3cb8d5b9e1d469a9ddb5807c91a9061"`
- `test "$(git rev-list -n 1 v0.1.0)" = "2124074d8028241f01a097f0ed48a84072aa43ba"`
- `test "$(git ls-remote origin 'refs/tags/v0.1.0^{}' | awk '{print $1}')" = "2124074d8028241f01a097f0ed48a84072aa43ba"`
- `release_commit=$(git rev-parse HEAD)`
- `test "$(git rev-list -n 1 <reviewed-tag>)" = "$release_commit"`
- `test "$(git ls-remote origin "refs/tags/<reviewed-tag>^{}" | awk '{print $1}')" = "$release_commit"`
- `test "$(git show <reviewed-tag>:VERSION)" = "<reviewed-tag-without-v>"`
- `git diff --name-only <reviewed-content-commit>..<release-commit>` contains
  only closure/bookkeeping paths under `implementation/`.
- Codex review runner per local canon.

## Risks

- The first release was already pushed before review. Mitigation: do not rewrite
  `v0.1.0`; publish reviewed changes as a later tag.
- The repo is both canon producer and canon consumer. Mitigation: keep
  `implementation/` explicitly local state and keep product status out of
  `canon/`.

## Review

This slice note must seal `ready` and be committed before bootstrap corrections
begin.
