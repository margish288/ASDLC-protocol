# Requirement Decomposition And Sub-Issue Policy

Agents must research and triage requirements before implementation, before creating new issues, and before creating sub-issues.

## Terms

Source or parent issue: the original issue, task, or requirement being triaged.

Implementation issue: a separate issue created from an oversized source issue. Implementation issues are not execution sub-issues; they are independent work items linked from the parent issue.

Execution sub-issue: a linked sub-issue created under a ready implementation issue after research, used to track separable implementation steps.

Parent issue description: the GitHub Issue body that must contain research summaries, linked work, progress, findings, fixes, blockers, and remaining work. A repo-local task file may stand in only for allowed `multiagent/tasks/` exceptions. When GitHub permissions allow, update the issue body directly rather than relying only on comments.

## Research First

Before deciding whether to split, create sub-issues, or code, agents must research the issue:

- read the issue description and comments
- read relevant repository docs and policy files
- inspect affected source files, tests, and configuration
- identify dependencies, risks, unknowns, and likely verification
- estimate issue points
- write a concise research summary in the parent GitHub Issue description

## Issue Points

Use issue points instead of size labels.

```text
1 issue point = 1 hour of expected implementation, verification, and documentation work
```

An implementation issue should fit in one focused PR and should not exceed 8 issue points. If a source issue is estimated over 8 issue points, split it into multiple separate implementation issues, not execution sub-issues. Each implementation issue must have its own issue point estimate and must be 8 issue points or less.

## Must Split When

Split a source issue into separate implementation issues when any of these are true:

- it contains more than one independent feature
- it touches unrelated modules
- it requires database + API + UI + deployment changes
- acceptance criteria can be delivered independently
- implementation likely needs multiple PRs
- review would be hard as a single PR
- estimated work is over 8 issue points
- sequencing or dependencies are unclear

## Do Not Split When

Do not split a source issue into separate implementation issues when:

- the task is already small
- splitting creates artificial tiny tasks
- changes must be atomic to be safe
- acceptance criteria cannot be independently verified
- the issue is 8 issue points or less, has clear acceptance criteria, and none of the must-split rules apply

## Oversized Parent Issue Rules

When research shows a source issue is over 8 issue points:

- label the parent `agent:needs-breakdown`
- create multiple separate implementation issues, not execution sub-issues
- estimate each implementation issue at 8 issue points or less
- include parent issue link, goal, acceptance criteria, dependencies, labels, issue points, verification expectations, and sequence order in each implementation issue
- update the parent issue description with the research summary, decomposition decision, linked implementation issue list, status checklist, blockers, and remaining work
- move the parent to `agent:split` after linked implementation issues are created
- leave the parent open until all implementation issues and their execution sub-issues are done

## Execution Sub-Issue Rules

For each ready implementation issue estimated at 8 issue points or less:

- research the implementation issue before coding
- create linked execution sub-issues when the work has separable steps worth tracking independently
- use the platform parent/sub-issue relationship when available so the parent issue visibly lists its sub-issues
- update the implementation issue description with the sub-issue list, sequence, status, and research summary
- work each execution sub-issue individually
- add findings, fixes, changed files, and verification evidence to each sub-issue description as work progresses
- summarize each completed sub-issue in the parent implementation issue description
- move the implementation issue to done only after every linked execution sub-issue is done

Do not create execution sub-issues when doing so creates artificial tiny tasks, hides an oversized requirement, or replaces the required split into separate implementation issues.

## Issue And Sub-Issue Requirements

Each implementation issue and execution sub-issue must include:

- parent issue link
- clear goal
- acceptance criteria
- dependencies
- research findings
- implementation or fix notes
- expected verification
- suggested labels
- issue point estimate
- sequence order

## Parent Issue Rules

When an issue has linked implementation issues or execution sub-issues:

- label parent `agent:split` when decomposition is complete
- remove `agent:ready` from oversized parent issues
- link all implementation issues and execution sub-issues
- use the parent issue description to track overall progress
- add concise finding and fix summaries from completed linked issues or sub-issues
- close or mark the parent done only when all linked implementation issues and execution sub-issues are done

## Human Input Required

Ask for human input instead of splitting when:

- product behavior is ambiguous
- acceptance criteria conflict
- scope cannot be reduced safely
- security, payment, or data behavior is unclear
- the parent issue does not provide enough context to write useful implementation issues or execution sub-issues
