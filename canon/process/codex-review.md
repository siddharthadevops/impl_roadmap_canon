# Codex Review Canon

Status: common canon

Codex is the per-round reviewer and one half of the double final seal. Each run
must be fresh, stateless, review-only, and saved as evidence under the consuming
project's git-ignored `implementation/review-work/` directory.

## Invocation

Default runner:

```bash
codex exec --sandbox read-only --output-last-message /path/to/last-message.txt - < /path/to/review-prompt.txt
```

The reviewer must not edit files. If a local project temporarily needs broader
filesystem access for reviews, record that deviation in local state and keep the
same no-edit instruction plus a before/after worktree check.

## Watchdog

macOS does not provide `timeout` by default, so run reviews with a watchdog:

```bash
OUT=implementation/review-work/<milestone>/<name>.md
mkdir -p "$(dirname "$OUT")"
RAW=$(mktemp); LAST=$(mktemp)
codex exec --sandbox read-only --output-last-message "$LAST" - < prompt.txt > "$RAW" 2>&1 &
CPID=$!
( sleep 480; pkill -9 -P "$CPID" 2>/dev/null; kill -9 "$CPID" 2>/dev/null ) &
WPID=$!
wait $CPID; STATUS=$?
kill $WPID 2>/dev/null; pkill -P "$WPID" 2>/dev/null
awk '/^([0-9]+\. )?F[0-9]+ \[P[0-3]\]/{p=1} p{print} /^VERDICT:/{exit}' "$LAST" > "$OUT"
grep -q '^VERDICT:' "$OUT" || grep -m1 '^VERDICT:' "$LAST" >> "$OUT"
echo "EXIT=$STATUS" >> "$OUT"
N=$(grep -oE 'VERDICT: [0-9]+' "$OUT" | grep -oE '[0-9]+' | head -1)
M=$(grep -cE '^([0-9]+\. )?F[0-9]+ \[P[0-3]\]' "$OUT")
{ ! grep -q '^VERDICT:' "$OUT" || [ "${N:-0}" != "${M:-0}" ]; } && \
  echo "INCOMPLETE: missing VERDICT or count mismatch (verdict ${N:-0}, captured $M)" | tee -a "$OUT" >&2
rm -f "$RAW" "$LAST"
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

Scratch evidence is regenerable and should not be committed.
