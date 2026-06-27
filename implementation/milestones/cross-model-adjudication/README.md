# Cross-Model Adjudication And Finding Verification

Status: closed

## Boundary

Amend the common process canon so doubts, reviewer disagreements, finding
verification, cross-model consultation, and operator escalation are explicit
process rules rather than implied review practice.

## Canonical Basis

- Common process: [`../../../canon/process/README.md`](../../../canon/process/README.md)
- Review runner: [`../../../canon/process/codex-review.md`](../../../canon/process/codex-review.md)
- Prior reviewed release: `v0.1.1`
- Operator direction: the orchestrator adjudicates, but all doubts and
  disagreements are discussed with a different LLM family when available; if no
  agreement is reached, the process stops and asks the operator.

## Reuse Posture

- Checked: existing `Reviews` and `Codex Review Canon` sections.
- Reused or extended: the current triage model (`fixed`, `rejected`, accepted
  debt), double seal, durable review log, and process-doc amendment mechanism.
- New machinery, if any: no automation; only explicit process language for
  consultations, adjudications, evidence checks, and escalation.
- Compatibility: existing local state remains valid; future reviews gain a
  stricter protocol for handling findings and doubts.

## Shared Contract

Reviewer output is evidence to investigate, not authority by itself. The
orchestrator owns triage, verifies every finding against files, diffs, tests, or
commands rather than memory or chat, consults a different LLM family for doubts
or disagreements when available, and stops for the operator when no clear
resolution remains.

## Slices

| Slice | Title | Status | Notes |
|---|---|---|---|
| 01 | Consultation and adjudication protocol | closed | Amended canon docs; publish reviewed tag `v0.2.0`. |

## Work Log

| Unit | Phase | Status | Review | Commit | Notes |
|---|---|---|---|---|---|
| Skeleton | doc | ready | doc-r6 + seal-a5 Codex/Claude | | Double seal clean; no accepted debt. |
| 01 | doc | ready | doc-r10 + seal-a1 Codex/Claude | 585fcd3 | Double seal clean; no accepted debt. |
| 01 | impl | review_clean | impl-r4 + seal-a4 Codex/Claude | a6fe5d4 | Release content reviewed; no accepted debt. |
| 01 | closure | closed | | | Closure/bookkeeping for reviewed tag `v0.2.0`. |

## Current Slice

None. S1 is closed.

## Continuation

S1 is closed. Continue by reading the global milestone index and roadmap before
opening any future canon change.
