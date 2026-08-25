# Agentic Workflow

This file is the agent-perspective map for where to go, what to read, and when to read it.

## Agent Reading Workflow

### 1. Entering The Repo

Read first:

1. `AGENTS.md`
2. `docs/agentic-workflow.md`
3. `docs/project-overview.md`

Use this step to understand the repository purpose, the agent operating rules, and the high-level project.

### 2. Before Choosing Work

Read:

1. `multiagent/protocol.md`
2. `multiagent/README.md`
3. `multiagent/policies/task-status.md`

Use this step to understand GitHub labels, optional local task statuses, priority order, issue points, and the lifecycle from triage to done.

### 3. Before Triaging A GitHub Issue

Read:

1. The GitHub Issue body and comments
2. `.github/ISSUE_TEMPLATE/agent_task.yml` or `.github/ISSUE_TEMPLATE/requirements_epic.yml`
3. `multiagent/protocol.md`
4. `multiagent/policies/decomposition.md`
5. `multiagent/templates/requirements-breakdown-template.md`

Use this step to classify the issue as `agent:ready`, `agent:needs-clarification`, `agent:needs-breakdown`, `agent:blocked`, or `agent:split`.

Research before creating issues, creating sub-issues, or coding. Record the research summary in the source GitHub Issue description. Use a repo-local task file only for an approved exception.

Do not code during triage.

### 4. Before Claiming Implementation

Read:

1. The ready GitHub Issue via `gh issue view`
2. `docs/setup.md`
3. `docs/testing.md`
4. `docs/conventions.md`
5. `multiagent/policies/permissions.md`
6. Any relevant policy files in `multiagent/policies/`

Use this step to confirm the goal, acceptance criteria, affected area, issue points, verification expectation, dependencies, approval requirements, and linked sub-issue plan.

Only claim implementation work from a GitHub Issue labeled `agent:ready`. The claimed issue must be estimated at 8 issue points or less. Use a local task only for repo-only work without a GitHub Issue, temporary local planning, explicit human request, or complex handoff notes.

### 5. Before Editing Code

Read the files that own the affected behavior.

Common paths:

- UI workflow: `[UI_ENTRYPOINTS]`
- API/backend: `[API_ENTRYPOINTS]`
- Domain logic: `[DOMAIN_PATHS]`
- Shared config/limits: `[CONFIG_PATHS]`
- Tests: `[TEST_PATHS]`

Use this step to understand local patterns before making changes.

### 6. While Working

Keep the GitHub Issue and PR updated with discoveries, scope changes, changed files, and test findings. Update a local task file only when the work falls under an allowed `multiagent/tasks/` exception.

Keep GitHub Issue descriptions updated when permissions allow:

- parent issues list linked implementation issues or execution sub-issues, status, summaries, blockers, and remaining work in the issue body, not only comments
- sub-issues record research findings, implementation or fix notes, changed files, and verification evidence
- parent issues are moved to done only after all linked implementation issues and execution sub-issues are done

When work becomes blocked or risky, read:

1. `multiagent/templates/handoff-template.md`
2. `multiagent/handoffs/README.md`

Then leave a handoff that another agent can continue from without chat history.

### 7. Before Review

Read:

1. `docs/testing.md`
2. `multiagent/policies/testing.md`
3. The active GitHub Issue and PR; read a local task file only when one exists for an approved exception
4. `multiagent/templates/changelog-entry-template.md`
5. `multiagent/logs/README.md`

Use this step to record changed files, commands run, test results, behavior verified, known limitations, and a new append-only status-event work log entry in the current monthly log.

Work logs must preserve every meaningful issue/task status event as a separate chronological line. Never rewrite an earlier log entry for the same issue or task.

When the status event happens during branch work, add the log entry before committing and include it in the same commit/PR as the related work or status change. Do not push completed work and then create a separate log-only follow-up commit for the matching status event.

## GitHub Issue Triage

GitHub Issues are the preferred backlog for agent work. New issues may start as `agent:needs-triage`.

This repo estimates implementation work with issue points:

```text
1 issue point = 1 hour of expected implementation, verification, and documentation work
```

Issues over 8 issue points should be split into separate implementation issues before coding. Do not use execution sub-issues as the split mechanism for an oversized source issue.

Before implementation, a triage agent researches the issue and checks whether the issue has:

- clear goal
- clear acceptance criteria
- enough context to begin
- test or verification expectation
- reasonable scope for one PR, estimated at 8 issue points or less
- no unresolved product decision
- known dependencies

## Labels

- `agent:needs-triage`: issue has not been classified yet.
- `agent:needs-clarification`: issue needs human input before implementation.
- `agent:needs-breakdown`: issue is over 8 issue points, too large, vague, or separable and must be decomposed before implementation.
- `agent:split`: parent issue has linked implementation issues or execution sub-issues and tracks overall progress.
- `agent:ready`: issue is clear, scoped, and ready for implementation.
- `agent:in-progress`: implementation is claimed and active.
- `agent:blocked`: issue cannot continue because of an external dependency or blocker.
- `agent:review`: implementation is ready for review.
- `agent:done`: work is merged, accepted, or explicitly complete.

## Breakdown

Agents should split large requirements when independent deliverables can be reviewed and verified separately.

Oversized requirements are split into separate implementation issues, not execution sub-issues. Each implementation issue is then researched and may create its own execution sub-issues when the implementation steps need separate tracking.

Each implementation issue or execution sub-issue should include:

- parent issue link
- goal
- acceptance criteria
- dependencies
- research findings
- implementation or fix notes
- expected verification
- suggested labels
- issue point estimate
- sequence order

Use `multiagent/policies/decomposition.md` for split rules and `multiagent/templates/requirements-breakdown-template.md` for recording a proposed breakdown.

## Issue Forms

- `.github/ISSUE_TEMPLATE/agent_task.yml` is for implementation-ready tasks intended to fit one PR.
- `.github/ISSUE_TEMPLATE/requirements_epic.yml` is for larger requirements that need triage and possible decomposition.
