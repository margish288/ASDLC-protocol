# Agentic Development Protocol

## Work Sources

Agents may work from:

1. GitHub Issues labeled `agent:ready`
2. Repo-local tasks in `multiagent/tasks/` with `status: ready`

GitHub Issues are preferred for team-visible work.

New GitHub Issues may start with `agent:needs-triage`. Agents must research and triage unclear or large requirements before implementation.

## Task Priority Order

Pick work in this order:

1. `priority:P0`
2. `priority:P1`
3. `priority:P2`
4. `priority:P3`

Within the same priority, pick the lowest sequence number or oldest ready issue.

## Requirement Research And Triage

Before claiming implementation work, agents must research and classify the issue or repo-local task.

Research checklist:

- read the issue or task description and comments
- read relevant repo docs and policy files
- inspect affected source files, tests, and configuration
- identify dependencies, risks, and unknowns
- estimate issue points
- write a concise research summary to the parent issue description or repo-local task file

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

## Local Task Status Flow

```text
backlog -> ready -> in_progress -> review -> done
                         |
                         v
                      blocked
```

## Claiming A Task

Only claim tasks classified as `agent:ready` or repo-local tasks with `status: ready`.

When claiming GitHub Issue `#123`:

1. Move label from `agent:ready` to `agent:in-progress`.
2. Comment with agent name and branch.
3. Create branch.
4. Create or update local task file.

Branch format must be one of:

```text
feature/123
bugfix/123
research/123
hotfix/123
```

Choose the prefix that matches the work type. Use the GitHub Issue number for the numeric suffix. For repo-only work without a GitHub Issue, use the local task number in the same position.

Task file format:

```text
multiagent/tasks/GH-123-short-title.md
```

For repo-only work, use:

```text
multiagent/tasks/TASK-000-short-title.md
```

## Working The Task

During implementation, update the task file when you discover:

- relevant files
- root cause
- design decisions
- blockers
- changed scope
- test findings

Also update GitHub Issue descriptions when permissions allow:

- parent issue description lists linked implementation issues or execution sub-issues and current status in the issue body, not only comments
- execution sub-issue descriptions include research findings, fixes, changed files, and verification evidence
- parent issue description receives a concise summary after each linked issue or sub-issue is completed

## Completing The Task

Before moving to `review`, update:

- task status
- done evidence
- changed files
- test results
- one-line log
- GitHub Issue labels
- PR link, if available

Do not move a parent issue to `agent:done` until every linked implementation issue and execution sub-issue is done.

## Blocking The Task

If blocked:

1. Set local task status to `blocked`.
2. Add blocker details.
3. Create handoff file.
4. Move GitHub label to `agent:blocked`, if using GitHub.
5. Comment on the issue with the blocker summary, if using GitHub.

## Stopping Mid-Task

Before stopping, agents must leave enough context for another agent to continue without reading chat history.
