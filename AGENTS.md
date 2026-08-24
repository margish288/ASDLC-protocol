# Agent Instructions

This repository is designed for agentic development. Any coding agent must be able to enter the repo, understand the project, pick work, complete it, and leave durable handoff context for the next human or agent.

## First Read Order

Before making changes, read these files:

1. `AGENTS.md`
2. `docs/agentic-workflow.md`
3. `docs/project-overview.md`
4. `docs/setup.md`
5. `docs/testing.md`
6. `docs/conventions.md`
7. `multiagent/protocol.md`
8. `multiagent/policies/permissions.md`
9. `multiagent/policies/decomposition.md` when triaging or splitting requirements
10. Relevant task file in `multiagent/tasks/`

## Project Summary

Project name: `[PROJECT_NAME]`

One-line purpose:

> `[WHAT_THIS_PROJECT_DOES]`

Primary stack:

- Language: `[LANGUAGE]`
- Framework: `[FRAMEWORK]`
- Styling/UI: `[STYLING_OR_UI]`
- Database: `[DATABASE_OR_NONE]`
- Package manager: `[PACKAGE_MANAGER]`
- Test runner: `[TEST_RUNNER]`
- Runtime: `[RUNTIME]`
- Deployment target: `[DEPLOYMENT_TARGET_OR_UNKNOWN]`

## Project Setup Notes

This protocol must be tailored to the target repository when installed:

- `[IMPORTANT_ENTRYPOINT_1]`
- `[IMPORTANT_ENTRYPOINT_2]`
- `[IMPORTANT_DOMAIN_FOLDER]`
- `[IMPORTANT_TEST_FOLDER]`
- `[KNOWN_ABSENCES_OR_LIMITATIONS]`

## Agent Workflow

Agents must work from either:

1. A GitHub Issue labeled `agent:ready`, or
2. A repo-local task file in `multiagent/tasks/`.

## Requirement Analysis Before Implementation

Agents must classify issues before coding.

Valid classifications:

- ready to implement
- needs clarification
- needs breakdown
- blocked

Use issue points for estimation:

```text
1 issue point = 1 hour of expected implementation, verification, and documentation work
```

Agents must not implement vague, oversized, or conflicting requirements. An issue estimated over 8 issue points is oversized and must be broken into smaller issues before implementation.

Agents may create sub-issues when the parent issue clearly contains separable work. Each sub-issue must have:

- parent issue link
- clear goal
- acceptance criteria
- dependencies
- suggested labels
- issue point estimate
- verification expectations
- sequence order

Agents must ask for human input when:

- product behavior is ambiguous
- acceptance criteria conflict
- scope cannot be reduced safely
- security, payment, or data behavior is unclear

Default flow:

1. Pull latest code when network and repository permissions allow.
2. Read required context files.
3. Find the highest-priority issue or task that is ready for triage or implementation.
4. Classify the requirement using `multiagent/protocol.md`.
5. Ask questions, mark blocked, or split the issue when it is not ready.
6. Claim only a ready task estimated at 8 issue points or less.
7. Create a task branch.
8. Implement only the scoped work.
9. Run relevant checks.
10. Update task file with evidence.
11. Update one-line log.
12. Open PR or leave handoff.
13. Move task status forward.

## Branch Naming

Use:

```text
agent/GH-<issue-number>-<short-title>
```

For repo-only tasks:

```text
agent/TASK-<task-number>-<short-title>
```

## Required Before Editing

Before editing code, the agent must understand:

- task goal
- acceptance criteria
- affected area
- expected tests
- policy restrictions
- current working tree status

## Definition Of Done

A task may only be marked `done` or `review` when:

- acceptance criteria are satisfied
- relevant tests/checks were run
- changed files are listed in the task file
- done evidence is written
- `multiagent/logs/<YYYY-MM>.md` is updated
- GitHub Issue or task status is updated
- PR is opened if code changed

## Forbidden Actions

Agents must not:

- commit secrets, tokens, `.env` files, private keys, or credentials
- rewrite git history unless explicitly instructed
- delete user work
- make unrelated refactors
- remove tests to make checks pass
- silently change public APIs
- make broad formatting-only changes
- mark work done without evidence
- leave incomplete work without handoff notes

## Human Approval Required

Ask for human approval before:

- adding new dependencies
- changing database schema or migrations
- changing authentication, authorization, billing, or security behavior
- modifying deployment configuration
- deleting files or large code paths
- changing public API contracts
- closing GitHub Issues without a PR or written explanation

## Handoff Requirement

If work is incomplete, update the task file and create a handoff in `multiagent/handoffs/`.

The handoff must include:

- current status
- what was changed
- what remains
- blockers
- commands run
- known risks
- recommended next step
