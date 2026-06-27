# Codex Review Canon

Status: common canon

Codex is the per-round reviewer and one half of the double final seal. Each run
must be fresh, stateless, review-only, and saved as evidence under the consuming
project's git-ignored `implementation/review-work/` directory.

## Invocation

Default Codex runner:

```bash
codex exec --dangerously-bypass-approvals-and-sandbox \
  --output-last-message /path/to/last-message.txt \
  - < /path/to/review-prompt.txt
```

When a process invokes Claude review commands, use the full-access Claude CLI
shape:

```bash
claude -p --model opus --effort max --permission-mode bypassPermissions \
  < /path/to/review-prompt.txt > /path/to/last-message.txt
```

Broad CLI access is review-only. Every broad review prompt must say that the
reviewer must not edit, create, delete, move, format, write files, or otherwise
modify the workspace. If a reviewer believes a file should change, it reports a
finding instead of changing it.

Local constraints still bind broad review access. Sensitive Local Exclusions in
local context must be honored, and stricter local process deviations win over
this common broad default.

Review prompts do not need to enumerate every possible directory. Reviewers may
inspect sibling repositories or dependency checkouts only when they are relevant
to the artifact and discovered while tracing that artifact.

## Worktree Check

Every broad Codex or Claude review run must compare worktree state before and
after the run. If tracked or untracked non-ignored files change, the output is
invalid and does not count as review or seal evidence.

Use a snapshot that covers dirty tracked state, staged changes, and untracked
non-ignored files, including content hashes for pre-existing untracked files:

```bash
snapshot_worktree() {
  git status --porcelain=v1
  git diff --no-ext-diff --binary
  git diff --cached --no-ext-diff --binary
  git ls-files --others --exclude-standard | while IFS= read -r f; do
    [ -f "$f" ] && shasum -a 256 "$f"
  done
}
```

Capture `PRE_STATE` immediately before the review command and `POST_STATE`
immediately after it exits. Append this marker to the saved output when they
differ:

```text
INVALID: worktree changed during review; discard this output and inspect git status/diff
```

The same worktree before/after invalidation applies to Claude CLI review runs.

## Watchdog

macOS does not provide `timeout` by default, so run Codex reviews with a
watchdog and the worktree check:

```bash
OUT=implementation/review-work/<milestone>/<name>.md
mkdir -p "$(dirname "$OUT")"
RAW=$(mktemp); LAST=$(mktemp); PRE_STATE=$(mktemp); POST_STATE=$(mktemp)
snapshot_worktree > "$PRE_STATE"
codex exec --dangerously-bypass-approvals-and-sandbox \
  --output-last-message "$LAST" - < prompt.txt > "$RAW" 2>&1 &
CPID=$!
( sleep 480; pkill -9 -P "$CPID" 2>/dev/null; kill -9 "$CPID" 2>/dev/null ) &
WPID=$!
wait $CPID; STATUS=$?
kill $WPID 2>/dev/null; pkill -P "$WPID" 2>/dev/null
snapshot_worktree > "$POST_STATE"
awk '/^([0-9]+\. )?F[0-9]+ \[P[0-3]\]/{p=1} p{print} /^VERDICT:/{exit}' "$LAST" > "$OUT"
grep -q '^VERDICT:' "$OUT" || grep -m1 '^VERDICT:' "$LAST" >> "$OUT"
echo "EXIT=$STATUS" >> "$OUT"
if ! cmp -s "$PRE_STATE" "$POST_STATE"; then
  echo "INVALID: worktree changed during review; discard this output and inspect git status/diff" | tee -a "$OUT" >&2
fi
N=$(grep -oE 'VERDICT: [0-9]+' "$OUT" | grep -oE '[0-9]+' | head -1)
M=$(grep -cE '^([0-9]+\. )?F[0-9]+ \[P[0-3]\]' "$OUT")
{ ! grep -q '^VERDICT:' "$OUT" || [ "${N:-0}" != "${M:-0}" ]; } && \
  echo "INCOMPLETE: missing VERDICT or count mismatch (verdict ${N:-0}, captured $M)" | tee -a "$OUT" >&2
rm -f "$RAW" "$LAST" "$PRE_STATE" "$POST_STATE"
```

Free-form adjudication or consultation rounds use the same launch/watch pattern
but save the whole last message plus `EXIT=`, with no `VERDICT:` parsing.
Their prompts must include the disputed finding or doubt, the orchestrator's
proposed resolution, and the files, diffs, tests, or commands already checked.
They are not review rounds: reviewer findings are claims, not facts; the
orchestrator still adjudicates after reading the different LLM family response,
including when the doubt came from a same-family sub-agent. If the issue remains
unresolved, stop and consult the operator.

## Prompt Shape

Keep prompts thin. Include:

- the artifact under review.
- the phase: skeleton, slice documentation, implementation, or process-doc.
- the canonical references the artifact depends on.
- the reuse gate.
- the local context constraints relevant to the review, including any support
  order or platform preference when the artifact proposes new machinery.
- any named brainstorming or named `_drafts` material as non-canonical context,
  checking that the reviewed artifact explicitly records the relevant
  **Adopt / Revise / Reject** decision instead of approving linked material.
- for process-doc work, review planning-material mechanism and link wording for
  brainstorming and `_drafts`; do not review product or architecture content
  unless the operator names that content as the review artifact.
- the severity rubric.
- the no-edit instruction.
- the rule that reviewer findings are claims, not facts.
- the rule that the orchestrator must verify findings against files, diffs,
  tests, or commands before triage.
- the rule that memory or chat is not evidence for triage.
- the rule that doubts and disagreements are discussed with a different LLM
  family when available, including doubts raised by a same-family sub-agent.
- the rule that unresolved disagreement, or unavailable cross-family
  consultation, stops and asks the operator.
- instructions to ignore prior review outputs, review logs, closures, and work
  log findings.
- output format.

Required output format:

```text
F01 [P1] path/to/file.md#Section - Finding text.
F02 [P2] path/to/file.md#Section - Finding text.
VERDICT: 2 findings
```

## Egress

The rule is simple: review CLIs send read material to external services. This
includes `codex exec` and Claude CLI review commands.

Reviewers must honor local Sensitive Local Exclusions and avoid
unrelated personal material.
Never send secrets, credentials, tokens, private keys, raw PII, or
raw sensitive operational data.
Also, operator confirmation does not override those never-send categories. If
review appears to require other sensitive material, stop for operator
confirmation or use redacted non-sensitive excerpts.

## Saving Output

Scratch evidence lives under:

```text
implementation/review-work/<milestone>/
implementation/review-work/process/
```

Durable evidence lives in tracked local state:

- milestone review output is summarized in the milestone's `review-log.md`.
- process-doc review output is summarized in `implementation/process/review-log.md`.
- slice debt is recorded in the closure.
- skeleton or process-doc debt is recorded in the relevant review log.

Scratch evidence is regenerable and should not be committed. `review-work/`
must not hold durable architecture material or guide material.
