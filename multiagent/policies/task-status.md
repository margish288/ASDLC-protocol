# Task Status Policy

The selected tracker owns current status. Local records use the Local values below; GitHub uses exactly one corresponding active `agent:*` status label. Change status only after its gate is satisfied, preserving priority/type/estimate labels.

## Status Mapping

| Local | GitHub label | Meaning |
| --- | --- | --- |
| backlog | agent:needs-triage | Captured, awaiting research |
| needs_clarification | agent:needs-clarification | Requires a human decision |
| needs_breakdown | agent:needs-breakdown | Requires decomposition |
| split | agent:split | Parent tracking linked work |
| ready | agent:ready | Researched, scoped, unblocked, at most eight points |
| in_progress | agent:in-progress | Claimed implementation |
| blocked | agent:blocked | Cannot proceed; blocker recorded |
| review | agent:review | Implementation and evidence ready for review |
| done | agent:done | Verified merged/accepted completion |
| cancelled | agent:cancelled | Explicitly abandoned/not planned; not successful completion |

Normal flow: `backlog -> ready -> in_progress -> review -> done`. Clarification and breakdown happen before ready. Work may become blocked or return from review for changes. A split parent aggregates its linked work rather than being claimed as an oversized implementation item.

## Readiness And Review

Ready requires research, clear acceptance criteria, verification expectations, known dependencies, no unresolved blocker, and an implementation estimate at most eight issue points. Use the decomposition policy for oversized work.

Review requires all of:

- scoped implementation is complete and acceptance criteria have evidence;
- relevant checks passed, or any unavailable checks and residual risk have explicit reviewer acceptance; failed required checks cannot be represented as passing;
- findings, fixes, changed files, and commands/results are in the authoritative record or linked PR;
- a PR exists when code changed;
- required execution children are review-ready or done, with evidence linked;
- a review status event is durably recorded using the logging policy.

A parent and its execution children may enter review together in one PR. Children do not need to be merged before their shared PR can be reviewed. Independent prerequisite work needed for integration must still be available and verified.

## Completion

Done requires all of:

- implementation acceptance criteria and required verification are satisfied;
- the associated PR is verified merged, or the human explicitly accepts the documented non-merged outcome (for example, completed research);
- every required linked implementation item and execution sub-issue is done;
- parent summaries include findings, fixes, and verification;
- the actual completion event is durable in the selected tracker and delivered or pending export under the logging policy.

Human acceptance never permits bypassing branch protection or treating unmerged code as deployed. Distinguish merged, accepted research, and deployed outcomes in the evidence. For a shared PR, after verifying merge, mark execution children done first, then the implementation parent, then any overall tracking parent.

Cancellation is a separate outcome with a reason and authorization; a closed GitHub issue alone is not proof of completion. If a required child is cancelled, its parent cannot be marked done until scope/acceptance criteria and required relationships are explicitly revised and the exclusion explained. Preserve historical links.

When reopening work, record why, clear the terminal status, reassess readiness and ownership, and append a new event. Never rewrite the old completion event.

## Labels And Metadata

For GitHub mode, create or verify the status labels in the table and these metadata labels during setup:

- Priority: `priority:P0`, `priority:P1`, `priority:P2`, `priority:P3`.
- Type: `type:feature`, `type:bug`, `type:research`, `type:refactor`, `type:docs`, `type:test`, `type:chore`.
- Estimate: `issue-points:1` through `issue-points:8`, and `issue-points:over-8`.

Local mode uses corresponding fields in task files and does not create GitHub labels. One issue point equals one hour of expected implementation, verification, and documentation. An over-eight estimate requires decomposition before implementation; do not use an atomic-work exception to silently bypass this gate.

Claiming and stale-owner handling are governed by the ownership policy. Every meaningful status transition follows the append-only logging policy; delivery bookkeeping is not a new product status transition.
