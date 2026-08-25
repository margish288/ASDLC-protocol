# Task Status Policy

## Local Task Statuses

GitHub labels are authoritative for normal work. These local statuses apply only to allowed `multiagent/tasks/` exception files.

`backlog`

Task exists but is not ready.

`ready`

Task has enough context and acceptance criteria.

`in_progress`

Task is claimed and actively being worked.

`blocked`

Task cannot continue without input or external fix.

`review`

Implementation is complete and ready for review.

`done`

Task is merged, accepted, or explicitly completed.

## GitHub Triage Labels

`agent:needs-triage`

Issue exists but has not been classified for readiness.

`agent:needs-clarification`

Issue needs human input before implementation.

`agent:needs-breakdown`

Issue is too large, vague, over 8 issue points, or separable and should be decomposed before implementation. Issues over 8 issue points must be split into separate implementation issues, not execution sub-issues.

`agent:split`

Parent issue has linked implementation issues or execution sub-issues and tracks overall progress.

`agent:ready`

Issue is clear, scoped, and ready for implementation.

`agent:blocked`

Issue cannot proceed because of an external dependency, missing access, or unresolved blocker.

## Issue Point Labels

Use issue points instead of size labels.

```text
1 issue point = 1 hour
```

Recommended labels:

- `issue-points:1`
- `issue-points:2`
- `issue-points:3`
- `issue-points:4`
- `issue-points:5`
- `issue-points:6`
- `issue-points:7`
- `issue-points:8`
- `issue-points:over-8`

Issues labeled `issue-points:over-8` should also be labeled `agent:needs-breakdown` unless a human explicitly approves keeping the work atomic.

## Priority Labels

- `priority:P0`: urgent priority; handle before P1/P2/P3.
- `priority:P1`: high priority; handle after P0 and before P2/P3.
- `priority:P2`: medium priority; handle after P0/P1 and before P3.
- `priority:P3`: low priority; handle after P0/P1/P2.

## Type Labels

- `type:feature`: new user-facing or product capability.
- `type:bug`: bug fix or regression work.
- `type:research`: research, investigation, or discovery work.
- `type:refactor`: internal code improvement that should preserve behavior.
- `type:docs`: documentation-only work.
- `type:test`: test coverage, test tooling, or verification work.
- `type:chore`: maintenance, housekeeping, or non-product task.

## Status Rules

Only one active agent should claim a GitHub Issue or allowed local task.

For normal work, use GitHub labels, issue body, issue comments, linked sub-issues, PRs, and PR comments as the authoritative status record. Do not create or update a local task file unless the work falls under an allowed `multiagent/tasks/` exception.

Every status transition must append a new work log entry in the current repo-level monthly log at `<protocol-root>/multiagent/logs/<YYYY-MM>.md`. Do not update or replace an earlier log entry for the same issue or task.

For local-only installs, monthly work logs stay ignored under `.agent-protocol/` and must not be committed or pushed. For explicit tracked-log installs, when a status transition happens during branch work, the log entry must be added before committing and included in the same commit/PR as the related work or status change. Do not push completed work and then create a separate log-only follow-up commit for the matching status transition.

Do not move a task to `review` unless:

- code is complete
- tests/checks are recorded
- done evidence is written in the GitHub Issue or PR
- linked execution sub-issues are done when the task has sub-issues
- parent issue description has summaries of findings, fixes, and verification evidence
- a new `review` work log entry has been appended
- PR exists when code changed

Do not move a task to `done` unless:

- PR is merged, or
- human explicitly accepts completion
- all linked implementation issues and execution sub-issues are done when the task is a parent issue
- a new `done` work log entry has been appended
