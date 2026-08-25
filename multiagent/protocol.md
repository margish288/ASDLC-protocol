# Agentic Development Protocol

## Protocol Root

In a local-only target repository install, the protocol root is `.agent-protocol/`.

In a tracked install or in this protocol-template source repository, the protocol root is the repository root.

Resolve protocol paths such as `multiagent/tasks/`, `multiagent/logs/`, and `docs/agentic-workflow.md` relative to the protocol root. GitHub Issues, PRs, source files, tests, package files, and product docs are target repository resources.

## Work Sources

GitHub Issues are the primary source of truth.

Agents must work from GitHub Issues labeled `agent:ready` by default. Use `gh issue list`, `gh issue view`, `gh issue edit`, `gh issue comment`, and related `gh pr` commands when GitHub access is available.

GitHub labels, issue body, issue comments, linked sub-issues, PRs, and PR comments are authoritative.

Agents must not create local task files for every GitHub Issue by default.

If GitHub cannot be reached or the agent cannot update issue bodies, labels, comments, PRs, or linked sub-issues, do not silently substitute local task files. Ask for access, mark the GitHub Issue blocked when possible, or use a local task file only when the work matches an allowed exception.

Use `<protocol-root>/multiagent/tasks/` only for:

- repo-only tasks without GitHub Issues
- temporary local planning
- explicit human request
- complex handoff that needs repo-local durable notes

Local task files are supplemental notes only. They must not replace or override GitHub Issues, labels, comments, PRs, or linked sub-issues.

New GitHub Issues may start with `agent:needs-triage`. Agents must research and triage unclear or large requirements before implementation.

## Task Priority Order

Pick work in this order:

1. `priority:P0`
2. `priority:P1`
3. `priority:P2`
4. `priority:P3`

Within the same priority, pick the lowest sequence number or oldest ready issue.

## Requirement Research And Triage

Before claiming implementation work, agents must research and classify the GitHub Issue. Use a repo-local task only for an allowed `multiagent/tasks/` exception.

Research checklist:

- read the GitHub Issue body and comments
- read relevant repo docs and policy files
- inspect affected source files, tests, and configuration
- identify dependencies, risks, and unknowns
- estimate issue points
- write a concise research summary to the parent GitHub Issue description

Readiness checklist:

- clear goal
- clear acceptance criteria
- enough context to begin
- test or verification expectation
- reasonable scope for one PR, estimated at 8 issue points or less
- no unresolved product decision
- dependencies are known

Triage outcomes:

- `agent:ready`: requirement is clear, scoped, and implementable.
- `agent:needs-clarification`: human input is needed before safe implementation.
- `agent:needs-breakdown`: requirement is over 8 issue points, too large, or separable and should be decomposed before implementation.
- `agent:blocked`: work cannot proceed because of an external dependency, access issue, or unresolved blocker.
- `agent:split`: parent requirement has linked implementation issues or execution sub-issues and tracks overall progress.

## Oversized Issues And Sub-Issues

If research estimates a source issue at over 8 issue points, agents must split it into multiple separate implementation issues, not execution sub-issues. Each implementation issue must be estimated at 8 issue points or less, linked from the parent issue, and worked independently.

For each ready implementation issue, agents must research the issue before coding. When the work contains separable execution steps, create linked execution sub-issues under that implementation issue, update the parent issue description with the sub-issue list and status, and work each sub-issue individually. Use the platform parent/sub-issue relationship when available so the parent issue visibly lists its sub-issues.

Each execution sub-issue description must include parent issue link, goal, acceptance criteria, dependencies, research findings, implementation or fix notes, expected verification, labels, issue point estimate, and sequence order.

Parent issue descriptions must stay current with linked implementation issues or sub-issues, research summaries, finding and fix summaries, blockers, and remaining work. When GitHub permissions allow, update the issue description/body directly rather than relying only on comments. A parent issue may only move to `agent:done` after all linked implementation issues and execution sub-issues are done.

Full lifecycle:

```text
Issue created
  -> agent:needs-triage
  -> triage agent researches
  -> if unclear: agent:needs-clarification
  -> if over 8 issue points or too large: agent:needs-breakdown
  -> create separate implementation issues
  -> parent becomes agent:split
  -> implementation issues become agent:ready
  -> implementation agent researches ready issue
  -> create execution sub-issues when needed
  -> agent:in-progress
  -> agent:review
  -> agent:done
```

Use issue points for estimation: 1 issue point = 1 hour of expected implementation, verification, and documentation work. Agents must not implement vague, oversized, conflicting, or risky requirements. Any issue estimated over 8 issue points must be split before implementation. Ask for human input when product behavior is ambiguous, acceptance criteria conflict, scope cannot be reduced safely, or security/payment/data behavior is unclear.

Use `multiagent/policies/decomposition.md` when deciding whether to split work or create execution sub-issues, and use `multiagent/templates/requirements-breakdown-template.md` to record the triage result.

## GitHub Issue Flow

```text
agent:needs-triage -> agent:ready -> agent:in-progress -> agent:review -> agent:done
         |                |
         |                v
         |          agent:blocked
         |
         +-> agent:needs-clarification
         |
         +-> agent:needs-breakdown -> implementation issues -> agent:split
```

## Local Task Exception Flow

Local tasks are exception-only. Use this flow only for repo-only tasks without GitHub Issues, temporary local planning, explicit human request, or complex handoff notes that need repo-local durability.

```text
backlog -> ready -> in_progress -> review -> done
                         |
                         v
                      blocked
```

## Claiming A Task

Only claim GitHub Issues classified as `agent:ready`. Use a repo-local task with `status: ready` only for an allowed `multiagent/tasks/` exception.

When claiming GitHub Issue `#123`:

1. Move label from `agent:ready` to `agent:in-progress`.
2. Comment with agent name and branch.
3. Create branch.
4. Update the issue body or comments with claim context.

Branch format must be one of:

```text
feature/123
bugfix/123
research/123
hotfix/123
```

Choose the prefix that matches the work type. Use the GitHub Issue number for the numeric suffix. For repo-only work without a GitHub Issue, use the local task number in the same position.

## Working The Task

During implementation, update the GitHub Issue or PR when you discover:

- relevant files
- root cause
- design decisions
- blockers
- changed scope
- test findings

Keep GitHub relationships and descriptions current:

- parent issue description lists linked implementation issues or execution sub-issues and current status in the issue body, not only comments
- execution sub-issue descriptions include research findings, fixes, changed files, and verification evidence
- parent issue description receives a concise summary after each linked issue or sub-issue is completed

Update a local task file only when the work falls under an allowed `multiagent/tasks/` exception.

## Completing The Task

Before moving to `review`, update:

- GitHub Issue status labels
- done evidence in the GitHub Issue or PR
- changed files
- test results
- new append-only status-event work log entry in the current monthly log, included with the same work commit/PR
- PR link, if available

Do not move a parent issue to `agent:done` until every linked implementation issue and execution sub-issue is done.

## Work Logs

Work logs under `<protocol-root>/multiagent/logs/` are repo-level monthly files. Use `<protocol-root>/multiagent/logs/<YYYY-MM>.md` for the calendar month in which the status event happened. Work logs are append-only supplemental audit history and do not replace GitHub as the source of truth.

Agents must add a new log line whenever they record a meaningful issue/task status event. This includes `agent:ready`, `agent:in-progress`, `agent:review`, and `agent:done` for GitHub Issues, and `ready`, `in_progress`, `review`, and `done` for repo-local tasks. Do not log routine progress chatter that does not change or document issue/task status.

Agents must never edit, replace, collapse, delete, or rewrite an earlier log entry for the same issue or task. Repeated issue/task IDs in the same monthly log are expected because the log is a chronological history, not a current-state table.

If later information becomes available, such as a PR number, merge commit, blocker resolution, or done status, append another line with that information instead of editing the earlier line.

In local-only installs, work logs are ignored local protocol files. Append local status-event entries, but do not commit or push them. GitHub Issue labels, issue body updates, comments, PRs, and PR comments are the shared status record.

In explicit tracked-log installs, when a status event happens during branch work, append the log entry before committing and include it in the same commit/PR as the related work or status change. Do not push completed work and then create a separate log-only follow-up commit for the matching status event.

If a `done` status is only known after merge, update the GitHub Issue or PR immediately. In explicit tracked-log installs, add the tracked monthly log entry in the merge/status-maintenance path used by the repository, not as an extra per-feature follow-up commit after the agent already pushed completed work.

## Blocking The Task

If blocked:

1. Move GitHub label to `agent:blocked`.
2. Update the issue body or comment with blocker details.
3. Add blocker context to the PR when one exists.
4. Create a repo-local handoff file under `<protocol-root>/multiagent/handoffs/` only for complex handoffs that need durable notes beyond GitHub or when explicitly requested.
5. If using an allowed local task file, set its status to `blocked`.

## Stopping Mid-Task

Before stopping, agents must leave enough context for another agent to continue without reading chat history.
