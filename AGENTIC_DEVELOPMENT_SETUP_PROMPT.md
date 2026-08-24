# Agentic Development Setup Prompt

Use this file as the reusable setup prompt for adding the same agentic development protocol to any project.

## How To Use

1. Open the target repository in your coding agent.
2. Paste the prompt in `Copy-Paste Setup Prompt`.
3. Ask the agent to inspect the repo first, then create or update the files.
4. Review the generated project-specific details before committing.
5. Create the GitHub labels listed in `GitHub Labels`.

Recommended first commit:

```text
Initialize agentic development protocol
```

## Copy-Paste Setup Prompt

```text
Set up a complete repo-local agentic development protocol for this project.

Important:
- Inspect the current repo first.
- Preserve existing project-specific content.
- Do not overwrite existing files blindly.
- If an equivalent file already exists, merge these rules into it.
- Fill templates with this project's real setup wherever possible.
- Keep placeholders only where the project does not yet define an answer.
- Do not implement any product feature.
- This task is documentation, workflow, and GitHub issue template setup only.

First inspect:
- README files
- package/dependency files
- framework config
- test config
- source folders
- docs/
- .github/ if present
- existing agent docs such as AGENTS.md, CLAUDE.md, SKILLS.md, .cursor/rules/

Create or update this structure:

AGENTS.md
SKILLS.md
CLAUDE.md
.cursor/rules/project.mdc
AGENTIC_DEVELOPMENT_SETUP_PROMPT.md

.github/
  ISSUE_TEMPLATE/
    agent_task.yml
    requirements_epic.yml

docs/
  agentic-workflow.md
  project-overview.md
  architecture.md
  setup.md
  testing.md
  conventions.md
  glossary.md
  decisions/
    ADR-0000-template.md

multiagent/
  README.md
  protocol.md
  tasks/
    README.md
  logs/
    README.md
    YYYY-MM.md
  handoffs/
    README.md
  policies/
    permissions.md
    git.md
    testing.md
    dependencies.md
    security.md
    task-status.md
    decomposition.md
  templates/
    task-template.md
    handoff-template.md
    changelog-entry-template.md
    adr-template.md
    requirements-breakdown-template.md

Core workflow requirements:
- Agents must classify GitHub Issues before coding.
- Valid classifications:
  - agent:needs-triage
  - agent:needs-clarification
  - agent:needs-breakdown
  - agent:split
  - agent:ready
  - agent:in-progress
  - agent:blocked
  - agent:review
  - agent:done
- Use issue points, not story points.
- 1 issue point = 1 hour of expected implementation, verification, and documentation work.
- Any issue over 8 issue points must be broken into smaller issues.
- Agents must not implement vague, oversized, conflicting, or risky requirements.
- Agents must ask for human input when product behavior is ambiguous, acceptance criteria conflict, scope cannot be reduced safely, or security/payment/data behavior is unclear.
- Agents should create GitHub sub-issues when a parent issue clearly contains separable work.
- Each sub-issue must have:
  - parent issue link
  - clear goal
  - acceptance criteria
  - dependencies
  - suggested labels
  - issue point estimate
  - verification expectations
  - sequence order

GitHub labels to create or verify:
- agent:needs-triage
- agent:needs-clarification
- agent:needs-breakdown
- agent:split
- agent:ready
- agent:in-progress
- agent:blocked
- agent:review
- agent:done
- priority:P0
- priority:P1
- priority:P2
- priority:P3
- type:feature
- type:bug
- type:research
- type:refactor
- type:docs
- type:test
- type:chore
- issue-points:1
- issue-points:2
- issue-points:3
- issue-points:4
- issue-points:5
- issue-points:6
- issue-points:7
- issue-points:8
- issue-points:over-8

After editing:
- List every changed file.
- Summarize what was added.
- Note assumptions.
- Note any existing files that were merged instead of replaced.
- Run markdown/YAML sanity checks where available.
- Do not mark any product issue as done.
```

## GitHub Labels

Create these labels in every project using this protocol.

```text
agent:needs-triage        Issue needs readiness triage before implementation.
agent:needs-clarification Issue needs human clarification before implementation.
agent:needs-breakdown     Issue is too large, vague, or over 8 issue points.
agent:split               Parent issue has been split into child issues.
agent:ready               Issue is clear, scoped, verified, and ready.
agent:in-progress         Agent has claimed and is actively working.
agent:blocked             Blocked by dependency, access, decision, or external issue.
agent:review              Implementation is complete and ready for review.
agent:done                Work is merged, accepted, or explicitly complete.

priority:P0               Urgent priority; handle before all other work.
priority:P1               High priority; handle after P0.
priority:P2               Medium priority; handle after P0/P1.
priority:P3               Low priority; handle after P0/P1/P2.

type:feature              New user-facing or product capability.
type:bug                  Bug fix or regression work.
type:research             Research, investigation, or discovery work.
type:refactor             Internal improvement that preserves behavior.
type:docs                 Documentation-only work.
type:test                 Test coverage, tooling, or verification work.
type:chore                Maintenance or housekeeping work.

issue-points:1            Estimated effort: 1 hour.
issue-points:2            Estimated effort: 2 hours.
issue-points:3            Estimated effort: 3 hours.
issue-points:4            Estimated effort: 4 hours.
issue-points:5            Estimated effort: 5 hours.
issue-points:6            Estimated effort: 6 hours.
issue-points:7            Estimated effort: 7 hours.
issue-points:8            Estimated effort: 8 hours.
issue-points:over-8       Over 8 hours; split into child issues.
```

Optional `gh` setup commands:

```bash
gh label create "agent:needs-triage" --color "fbca04" --description "Issue needs readiness triage before implementation."
gh label create "agent:needs-clarification" --color "d93f0b" --description "Issue needs human clarification before implementation."
gh label create "agent:needs-breakdown" --color "c5def5" --description "Issue is too large, vague, or over 8 issue points."
gh label create "agent:split" --color "bfdadc" --description "Parent issue has been split into child issues."
gh label create "agent:ready" --color "6128a8" --description "Clear scope, criteria, verification, dependencies; ready."
gh label create "agent:in-progress" --color "6d47f3" --description "Agent has claimed and is actively working."
gh label create "agent:blocked" --color "3b1fec" --description "Blocked by dependency, access, decision, or external issue."
gh label create "agent:review" --color "e9e60c" --description "Implementation is complete and ready for review."
gh label create "agent:done" --color "0e8a16" --description "Work is merged, accepted, or explicitly complete."
gh label create "priority:P0" --color "b60205" --description "Urgent priority; handle before all other work."
gh label create "priority:P1" --color "b60205" --description "High priority; handle after P0."
gh label create "priority:P2" --color "fbca04" --description "Medium priority; handle after P0/P1."
gh label create "priority:P3" --color "0e8a16" --description "Low priority; handle after P0/P1/P2."
gh label create "type:feature" --color "0e8a16" --description "New user-facing or product capability."
gh label create "type:bug" --color "d93f0b" --description "Bug fix or regression work."
gh label create "type:research" --color "0e7583" --description "Research, investigation, or discovery work."
gh label create "type:refactor" --color "c5def5" --description "Internal improvement that preserves behavior."
gh label create "type:docs" --color "0a938f" --description "Documentation-only work."
gh label create "type:test" --color "5319e7" --description "Test coverage, tooling, or verification work."
gh label create "type:chore" --color "ededed" --description "Maintenance or housekeeping work."
gh label create "issue-points:1" --color "c2e0c6" --description "Estimated effort: 1 hour."
gh label create "issue-points:2" --color "c2e0c6" --description "Estimated effort: 2 hours."
gh label create "issue-points:3" --color "c2e0c6" --description "Estimated effort: 3 hours."
gh label create "issue-points:4" --color "fbca04" --description "Estimated effort: 4 hours."
gh label create "issue-points:5" --color "fbca04" --description "Estimated effort: 5 hours."
gh label create "issue-points:6" --color "fbca04" --description "Estimated effort: 6 hours."
gh label create "issue-points:7" --color "d93f0b" --description "Estimated effort: 7 hours."
gh label create "issue-points:8" --color "d93f0b" --description "Estimated effort: 8 hours."
gh label create "issue-points:over-8" --color "b60205" --description "Over 8 hours; split into child issues."
```

## File Templates

Use these templates as the baseline. Replace bracketed placeholders with project-specific values.

### `AGENTS.md`

````md
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

This protocol is tailored to the current repository:

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

- clear goal
- acceptance criteria
- dependencies
- suggested labels
- issue point estimate
- verification expectations

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
````

### `SKILLS.md`

````md
# Project Skills

This file describes the project-specific knowledge and capabilities agents should develop while working here.

## Required Project Knowledge

Agents working on this repo should understand:

- `[PROJECT_ARCHITECTURE]`
- `[LOCAL_SETUP]`
- `[TEST_COMMANDS]`
- `[CODE_CONVENTIONS]`
- `[DEPLOYMENT_FLOW_OR_UNKNOWN]`
- GitHub Issue workflow and task handoff protocol
- Requirement triage and decomposition protocol

## Common Work Types

### Feature Work

Expected agent behavior:

- read related files first
- implement only scoped behavior
- add or update tests
- update docs if behavior changes
- preserve existing API/contract shapes unless the task explicitly says otherwise
- provide done evidence

### Bug Fixes

Expected agent behavior:

- reproduce or reason about the bug
- identify root cause
- add regression test where practical
- keep fix minimal
- document changed behavior

### Refactors

Expected agent behavior:

- refactor only inside task scope
- preserve behavior
- run broad enough tests
- avoid mixed feature/refactor commits

### Documentation

Expected agent behavior:

- keep docs factual and current
- avoid speculative claims
- link to relevant files when possible

### Requirement Triage And Decomposition

Expected agent behavior:

- read the full requirement carefully before coding
- identify ambiguity, missing acceptance criteria, and conflicting constraints
- estimate issue points, where 1 issue point = 1 hour
- decide whether the task fits one focused PR and stays at 8 issue points or less
- split requirements over 8 issue points into smaller GitHub issues when work is separable
- give each sub-issue a clear goal, acceptance criteria, dependencies, suggested labels, issue point estimate, verification expectations, and sequence
- sequence dependent work so foundational changes come before UI, integration, or rollout work
- ask for human input when product behavior, data handling, security, payment, or scope boundaries are unclear
- avoid coding until the issue is classified as ready

## Project-Specific Commands

```bash
# Install dependencies
[INSTALL_COMMAND]

# Run development server
[DEV_COMMAND]

# Run tests
[TEST_COMMAND]

# Run typecheck
[TYPECHECK_COMMAND]

# Run lint
[LINT_COMMAND]

# Run build
[BUILD_COMMAND]
```

## Dangerous Areas

Agents need extra care around:

- authentication: `[NOTES]`
- authorization: `[NOTES]`
- database: `[NOTES]`
- migrations: `[NOTES]`
- payment/billing: `[NOTES]`
- deployment: `[NOTES]`
- generated files: `[NOTES]`
- external integrations: `[NOTES]`
- user data/privacy: `[NOTES]`

## Preferred Patterns

- `[PATTERN_1]`
- `[PATTERN_2]`
- `[PATTERN_3]`

## Avoided Patterns

- `[ANTI_PATTERN_1]`
- `[ANTI_PATTERN_2]`
- `[ANTI_PATTERN_3]`
````

### `CLAUDE.md`

````md
# Claude Instructions

This repo uses a shared agentic development protocol.

Before making changes, read:

1. `AGENTS.md`
2. `docs/agentic-workflow.md`
3. `multiagent/protocol.md`
4. Relevant files under `multiagent/policies/`
5. The active task file under `multiagent/tasks/`

Follow `AGENTS.md` as the source of truth.
````

### `.cursor/rules/project.mdc`

````md
---
description: Project-wide agentic development rules
alwaysApply: true
---

This repo uses a shared agentic development protocol.

Before editing code:

1. Read `AGENTS.md`
2. Read `docs/agentic-workflow.md`
3. Read `multiagent/protocol.md`
4. Read relevant policy files in `multiagent/policies/`
5. Classify the requirement before implementation
6. Work only from a GitHub Issue labeled `agent:ready` or a `multiagent/tasks/` task file with `status: ready`

Follow `AGENTS.md` as the source of truth.
````

### `docs/agentic-workflow.md`

````md
# Agentic Workflow

This file is the agent-perspective map for where to go, what to read, and when to read it.

## Agent Reading Workflow

### 1. Entering The Repo

Read first:

1. `AGENTS.md`
2. `docs/agentic-workflow.md`
3. `docs/project-overview.md`

Use this step to understand the repository purpose, the agent operating rules, and the high-level product.

### 2. Before Choosing Work

Read:

1. `multiagent/protocol.md`
2. `multiagent/README.md`
3. `multiagent/policies/task-status.md`

Use this step to understand GitHub labels, task statuses, priority order, issue points, and the lifecycle from triage to done.

### 3. Before Triaging A GitHub Issue

Read:

1. The GitHub Issue body and comments
2. `.github/ISSUE_TEMPLATE/agent_task.yml` or `.github/ISSUE_TEMPLATE/requirements_epic.yml`
3. `multiagent/protocol.md`
4. `multiagent/policies/decomposition.md`
5. `multiagent/templates/requirements-breakdown-template.md`

Use this step to classify the issue as `agent:ready`, `agent:needs-clarification`, `agent:needs-breakdown`, `agent:blocked`, or `agent:split`.

Do not code during triage.

### 4. Before Claiming Implementation

Read:

1. The ready GitHub Issue or local task file
2. `docs/setup.md`
3. `docs/testing.md`
4. `docs/conventions.md`
5. `multiagent/policies/permissions.md`
6. Any relevant policy files in `multiagent/policies/`

Use this step to confirm the goal, acceptance criteria, affected area, issue points, verification expectation, dependencies, and approval requirements.

Only claim work labeled `agent:ready` or a local task with `status: ready`.

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

Keep the active task file in `multiagent/tasks/` updated with discoveries, scope changes, changed files, and test findings.

When work becomes blocked or risky, read:

1. `multiagent/templates/handoff-template.md`
2. `multiagent/handoffs/README.md`

Then leave a handoff that another agent can continue from without chat history.

### 7. Before Review

Read:

1. `docs/testing.md`
2. `multiagent/policies/testing.md`
3. The active task file
4. `multiagent/templates/changelog-entry-template.md`
5. `multiagent/logs/README.md`

Use this step to record changed files, commands run, test results, behavior verified, known limitations, and the one-line work log entry.

## GitHub Issue Triage

GitHub Issues are the preferred backlog for agent work. New issues may start as `agent:needs-triage`.

This repo estimates implementation work with issue points:

```text
1 issue point = 1 hour of expected implementation, verification, and documentation work
```

Issues over 8 issue points should be split into smaller issues before coding.

Before implementation, a triage agent checks whether the issue has:

- clear goal
- clear acceptance criteria
- enough context to begin
- test or verification expectation
- reasonable scope for one PR, estimated at 8 issue points or less
- no unresolved product decision
- known dependencies

## Labels

- `agent:needs-triage`: issue has not been classified yet.
- `agent:needs-clarification`: human input is needed before implementation.
- `agent:needs-breakdown`: issue is over 8 issue points, too large, vague, or separable.
- `agent:split`: parent issue has child issues and tracks overall progress.
- `agent:ready`: issue is clear, scoped, and ready for implementation.
- `agent:in-progress`: implementation is claimed and active.
- `agent:blocked`: issue cannot continue because of an external dependency or blocker.
- `agent:review`: implementation is ready for review.
- `agent:done`: work is merged, accepted, or explicitly complete.

## Breakdown

Agents should split large requirements when independent deliverables can be reviewed and verified separately.

Each child issue should include:

- parent issue link
- goal
- acceptance criteria
- dependencies
- expected verification
- suggested labels
- issue point estimate
- sequence order

Use `multiagent/policies/decomposition.md` for split rules and `multiagent/templates/requirements-breakdown-template.md` for recording a proposed breakdown.

## Issue Forms

- `.github/ISSUE_TEMPLATE/agent_task.yml` is for implementation-ready tasks intended to fit one PR.
- `.github/ISSUE_TEMPLATE/requirements_epic.yml` is for larger requirements that need triage and possible decomposition.
````

### `docs/project-overview.md`

````md
# Project Overview

## What This Project Does

`[Explain the product/project in plain language.]`

## Primary Users

- User type 1:
- User type 2:

## Main Capabilities

- Capability 1
- Capability 2
- Capability 3

## Non-Goals

This project does not aim to:

- Non-goal 1
- Non-goal 2

## Important External Systems

- GitHub:
- Database:
- APIs:
- Deployment:
- Monitoring:

## Current Development Priorities

- Priority 1
- Priority 2
- Priority 3
````

### `docs/architecture.md`

````md
# Architecture

## High-Level Flow

```text
[USER_OR_SYSTEM_INPUT]
  -> [ENTRYPOINT]
  -> [CORE_DOMAIN_LOGIC]
  -> [PERSISTENCE_OR_EXTERNAL_SYSTEMS]
  -> [OUTPUT]
```

## Application Layers

### UI / Client

- `[UI_PATH]`: `[DESCRIPTION]`

### API / Backend

- `[API_PATH]`: `[DESCRIPTION]`

### Domain Libraries

- `[DOMAIN_PATH]`: `[DESCRIPTION]`

### Data / Persistence

- `[DATA_PATH_OR_NONE]`: `[DESCRIPTION]`

## Important Runtime Details

- Runtime:
- Environment variables:
- External services:
- Generated files:
- Known limitations:

## Testing Architecture

- Unit tests:
- Integration tests:
- E2E/manual checks:
- CI:
````

### `docs/setup.md`

````md
# Setup

## Requirements

- Runtime:
- Package manager:
- Database:
- Other services:

## Install

```bash
[INSTALL_COMMAND]
```

## Environment

Required environment variables:

```text
EXAMPLE_ENV=
```

Use `.env.example` if available. Never commit real secrets.

## Run Locally

```bash
[DEV_COMMAND]
```

## Useful Commands

```bash
[TEST_COMMAND]
[TYPECHECK_COMMAND]
[LINT_COMMAND]
[BUILD_COMMAND]
```

## Common Problems

### Problem

Fix:

```bash
[FIX_COMMAND]
```
````

### `docs/testing.md`

````md
# Testing

## Test Commands

```bash
# all tests
[TEST_COMMAND]

# unit tests
[UNIT_TEST_COMMAND]

# typecheck
[TYPECHECK_COMMAND]

# lint
[LINT_COMMAND]

# build
[BUILD_COMMAND]
```

## When To Run What

- Small isolated change:
- API/backend change:
- UI change:
- Shared logic change:
- Dependency/config change:

## Required Evidence

Agents must record test evidence in the active task file.

At minimum, include:

- command run
- pass/fail result
- relevant failure summary
- skipped checks and reason
- manual verification notes, when applicable
````

### `docs/conventions.md`

````md
# Conventions

## Code Style

- Convention 1
- Convention 2

## File Organization

- Convention 1
- Convention 2

## Naming

- Branches:
- Components/classes:
- Functions:
- Tests:

## Error Handling

- Pattern 1
- Pattern 2

## Documentation

Update docs when behavior, setup, commands, architecture, limits, security assumptions, or public contracts change.
````

### `docs/glossary.md`

````md
# Glossary

## Agent

An AI coding assistant or automation working in the repository.

## Agentic Development Protocol

The repo-local workflow in `AGENTS.md` and `multiagent/` that defines how agents pick up tasks, record evidence, and hand off work.

## Issue Point

An estimate where 1 issue point = 1 hour of expected implementation, verification, and documentation work.

## Handoff

A durable note in `multiagent/handoffs/` explaining incomplete work so another human or agent can continue without chat history.

## Done Evidence

The changed files, commands, test results, behavior verification, and limitations recorded before moving a task to review or done.

## [PROJECT_TERM]

[Definition]
````

### `docs/decisions/ADR-0000-template.md`

````md
# ADR-0000: Decision Title

Date: YYYY-MM-DD

## Status

Proposed / Accepted / Superseded

## Context

What problem or tradeoff led to this decision?

## Decision

What did we decide?

## Consequences

Positive:

- Item

Negative:

- Item

## Alternatives Considered

- Alternative 1
- Alternative 2
````

### `multiagent/README.md`

````md
# Multiagent Workflow

This directory contains the repo-local operating system for agents.

GitHub Issues are the backlog. Files in this directory are the durable working memory.

GitHub Issues may start as `agent:needs-triage`. Agents should classify and, when needed, decompose requirements before implementation.

This workflow estimates work with issue points: 1 issue point = 1 hour of expected implementation, verification, and documentation work. Issues over 8 issue points should be split before coding.

For the agent-perspective read order, use `docs/agentic-workflow.md`.

## Directory Map

```text
multiagent/
  protocol.md              Process agents must follow
  tasks/                   One task mirror per active task
  logs/                    One-line chronological work log
  handoffs/                Incomplete work handoffs
  policies/                Permissions, restrictions, and safety rules
  templates/               Copy-ready templates
```

## Requirement Triage

Agents must not blindly implement large or unclear issues.

Before coding, classify each issue as:

- `agent:ready`
- `agent:needs-clarification`
- `agent:needs-breakdown`
- `agent:blocked`
- `agent:split`

If an issue contains separable work or is over 8 issue points, use `multiagent/policies/decomposition.md` and `multiagent/templates/requirements-breakdown-template.md` to propose child issues with acceptance criteria, dependencies, labels, issue point estimates, verification expectations, and sequence.

## Core Principle

No important agent context should live only in chat.

If an agent discovers something important, it must be written into:

- the task file
- a handoff file
- docs
- an ADR
- or the one-line log
````

### `multiagent/protocol.md`

````md
# Agentic Development Protocol

## Work Sources

Agents may work from:

1. GitHub Issues labeled `agent:ready`
2. Repo-local tasks in `multiagent/tasks/` with `status: ready`

GitHub Issues are preferred for team-visible work.

New GitHub Issues may start with `agent:needs-triage`. Agents must triage unclear or large requirements before implementation.

## Task Priority Order

Pick work in this order:

1. `priority:P0`
2. `priority:P1`
3. `priority:P2`
4. `priority:P3`

Within the same priority, pick the lowest sequence number or oldest ready issue.

## Requirement Triage

Before claiming implementation work, agents must classify the issue or repo-local task.

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
- `agent:needs-breakdown`: requirement is over 8 issue points, too large, or separable and should be decomposed.
- `agent:blocked`: work cannot proceed because of an external dependency, access issue, or unresolved blocker.
- `agent:split`: parent requirement has been decomposed into child issues.

Full lifecycle:

```text
Issue created
  -> agent:needs-triage
  -> triage agent reviews
  -> if unclear: agent:needs-clarification
  -> if over 8 issue points or too large: agent:needs-breakdown
  -> create sub-issues
  -> parent becomes agent:split
  -> child issues become agent:ready
  -> implementation agent claims ready issue
  -> agent:in-progress
  -> agent:review
  -> agent:done
```

Use issue points for estimation: 1 issue point = 1 hour of expected implementation, verification, and documentation work. Agents must not implement vague, oversized, conflicting, or risky requirements. Any issue estimated over 8 issue points must be split before implementation. Ask for human input when product behavior is ambiguous, acceptance criteria conflict, scope cannot be reduced safely, or security/payment/data behavior is unclear.

Use `multiagent/policies/decomposition.md` when deciding whether to split work, and use `multiagent/templates/requirements-breakdown-template.md` to record the triage result.

## GitHub Issue Flow

```text
agent:needs-triage -> agent:ready -> agent:in-progress -> agent:review -> agent:done
         |                |
         |                v
         |          agent:blocked
         |
         +-> agent:needs-clarification
         |
         +-> agent:needs-breakdown -> child issues -> agent:split
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

Branch format:

```text
agent/GH-123-short-title
```

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

## Completing The Task

Before moving to `review`, update:

- task status
- done evidence
- changed files
- test results
- one-line log
- GitHub Issue labels
- PR link, if available

## Blocking The Task

If blocked:

1. Set local task status to `blocked`.
2. Add blocker details.
3. Create handoff file.
4. Move GitHub label to `agent:blocked`, if using GitHub.
5. Comment on the issue with the blocker summary, if using GitHub.

## Stopping Mid-Task

Before stopping, agents must leave enough context for another agent to continue without reading chat history.
````

### `multiagent/tasks/README.md`

````md
# Tasks

Create one task file per active GitHub Issue or repo-local task.

Use `multiagent/templates/task-template.md` as the starting point.

## Naming

GitHub issue tasks:

```text
GH-123-short-title.md
```

Repo-only tasks:

```text
TASK-000-short-title.md
```

## Required Practice

- Do not start implementation until the task is `ready`.
- Mark unclear tasks as `blocked` or keep them out of `ready` until questions are answered.
- Split large repo-local tasks into smaller task files when they contain separable work.
- Keep status and branch current.
- Record discoveries while working.
- List changed files before review.
- Record commands and results.
- Link the PR when code changes.
- Add handoff notes if incomplete or risky.
````

### `multiagent/logs/README.md`

````md
# Work Logs

Keep one-line chronological task entries here.

Use one file per month:

```text
YYYY-MM.md
```

For example, work done in August 2026 belongs in:

```text
2026-08.md
```

Copy the format from `multiagent/logs/YYYY-MM.md`.
````

### `multiagent/logs/YYYY-MM.md`

````md
# Work Log: YYYY-MM

Format:

```text
YYYY-MM-DD | task | status | summary | agent | branch/pr
```

## Entries

YYYY-MM-DD | GH-000 | review | Short summary of completed work | agent-name | branch/pr
````

### `multiagent/handoffs/README.md`

````md
# Handoffs

Use this directory when work is incomplete, blocked, risky, or needs another agent or human to continue.

Start from `multiagent/templates/handoff-template.md`.

## Naming

```text
GH-123-short-title-handoff.md
TASK-000-short-title-handoff.md
```

## Required Contents

- current status
- what changed
- what remains
- blockers
- commands run
- important context
- risks
- recommended next step
````

### `multiagent/policies/permissions.md`

````md
# Agent Permissions Policy

## Green Actions

Agents may do these without approval when scoped to the active task:

- read repository files
- edit source files
- add or update tests
- update documentation
- create task branches
- classify issues for readiness
- create GitHub sub-issues from a clear parent requirement
- update non-terminal GitHub triage labels
- update task files
- update one-line logs
- add handoff notes
- run local test/build/lint commands

## Yellow Actions

Agents may do these only with written justification in the task file:

- refactor shared abstractions
- modify config files
- update CI workflows
- change public interfaces
- edit generated files
- add feature flags
- touch security-sensitive code

## Red Actions

Agents must get explicit human approval before:

- adding dependencies
- changing database schema
- writing migrations
- changing auth or permission behavior
- changing billing/payment behavior
- deleting major code paths
- rewriting git history
- changing deployment secrets/config
- closing issues without PR/review
````

### `multiagent/policies/git.md`

````md
# Git Policy

## Required

- Start from latest `main` unless task says otherwise.
- Use a task branch.
- Keep commits scoped to the task.
- Do not mix unrelated cleanup with feature work.
- Check working tree before and after changes.

## Branch Names

GitHub issue tasks:

```text
agent/GH-<issue-number>-<short-title>
```

Repo-only tasks:

```text
agent/TASK-<task-number>-<short-title>
```

## Forbidden

Agents must not:

- run `git reset --hard`
- force push
- rewrite history
- delete branches with unmerged work
- revert user changes unless explicitly instructed

## Commit Messages

Use:

```text
GH-123: short imperative summary
```

For repo-only tasks:

```text
TASK-000: short imperative summary
```
````

### `multiagent/policies/testing.md`

````md
# Testing Policy

## Required

Agents must run tests relevant to changed behavior.

At minimum, record:

- command run
- result
- failures
- skipped checks
- reason if a check could not be run

## Test Selection

Use the narrowest meaningful check first, then broader checks when risk is higher.

Examples:

- small utility change: unit test
- API behavior change: unit/integration test
- UI workflow change: component/e2e/manual verification
- shared abstraction change: broader test suite
- config/build change: build command

## Project Commands

```bash
[TEST_COMMAND]
[TYPECHECK_COMMAND]
[LINT_COMMAND]
[BUILD_COMMAND]
```

## Done Evidence

A task cannot move to `review` without test evidence.

If tests cannot be run, explain why and mark residual risk.
````

### `multiagent/policies/dependencies.md`

````md
# Dependency Policy

Adding dependencies requires human approval unless the task explicitly authorizes it.

## Current Dependency Profile

- Runtime: `[RUNTIME_DEPS]`
- Development: `[DEV_DEPS]`
- Package manager: `[PACKAGE_MANAGER]`

## Before Proposing A Dependency

Document:

- package name
- reason it is needed
- alternatives considered
- maintenance risk
- license concern, if any
- expected bundle/runtime impact

## Forbidden

Do not add dependencies for trivial helpers, formatting convenience, or avoidable wrappers.
````

### `multiagent/policies/security.md`

````md
# Security Policy

## Secrets

Never commit:

- `.env`
- `.env.local`
- API keys
- tokens
- private keys
- credentials
- production config values

## Sensitive Areas

Human approval is required before changing:

- authentication
- authorization
- session handling
- password logic
- token handling
- billing/payment logic
- data deletion
- personally identifiable information handling

## Project-Specific Security Notes

- `[SECURITY_NOTE_1]`
- `[SECURITY_NOTE_2]`
- `[SECURITY_NOTE_3]`

## Required For Security-Sensitive Tasks

Record in the task file:

- threat or risk considered
- changed behavior
- tests run
- remaining risk
````

### `multiagent/policies/task-status.md`

````md
# Task Status Policy

## Statuses

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

Issue is too large, vague, over 8 issue points, or separable and should be decomposed.

`agent:split`

Parent issue has been decomposed into child issues and tracks overall progress.

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

Only one active agent should claim a task.

Do not move a task to `review` unless:

- code is complete
- tests/checks are recorded
- done evidence is written
- PR exists when code changed

Do not move a task to `done` unless:

- PR is merged, or
- human explicitly accepts completion
````

### `multiagent/policies/decomposition.md`

````md
# Requirement Decomposition Policy

Agents must triage requirements before implementation and split work when a single issue is too large, vague, risky, or made of separable deliverables.

## Issue Points

Use issue points instead of size labels.

```text
1 issue point = 1 hour of expected implementation, verification, and documentation work
```

An issue should fit in one focused PR and should not exceed 8 issue points. If the estimate is over 8 issue points, split the work into child issues. Each child issue should have its own issue point estimate and should be 8 issue points or less.

## Must Split When

Split a task when any of these are true:

- it contains more than one independent feature
- it touches unrelated modules
- it requires database + API + UI + deployment changes
- acceptance criteria can be delivered independently
- implementation likely needs multiple PRs
- review would be hard as a single PR
- estimated work is over 8 issue points
- sequencing or dependencies are unclear

## Do Not Split When

Do not split a task when:

- the task is already small
- splitting creates artificial tiny tasks
- changes must be atomic to be safe
- acceptance criteria cannot be independently verified
- the issue is 8 issue points or less, has clear acceptance criteria, and none of the must-split rules apply

## Sub-Issue Requirements

Each sub-issue must include:

- parent issue link
- clear goal
- acceptance criteria
- dependencies
- expected verification
- suggested labels
- issue point estimate
- sequence order

## Parent Issue Rules

When an issue is split:

- label parent `agent:split`
- remove `agent:ready`
- link all child issues
- use the parent to track overall progress
- close the parent only when children are done

## Human Input Required

Ask for human input instead of splitting when:

- product behavior is ambiguous
- acceptance criteria conflict
- scope cannot be reduced safely
- security, payment, or data behavior is unclear
- the parent issue does not provide enough context to write useful child issues
````

### `multiagent/templates/task-template.md`

````md
---
id: GH-000
source: github
github_issue: 000
title: ""
status: ready
priority: P2
sequence: 000
issue_points:
depends_on: []
claimed_by:
branch:
pr:
created_at: YYYY-MM-DD
updated_at: YYYY-MM-DD
---

# GH-000: Task Title

## Goal

Describe the outcome this task should achieve.

## Acceptance Criteria

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## Context

Relevant background, links, issue notes, or constraints.

## Affected Areas

- `path/to/file`
- `path/to/module`

## Issue Points

Estimate total implementation, verification, and documentation work.

```text
1 issue point = 1 hour
```

- Estimate:
- Over 8 issue points:
  - [ ] yes, split before implementation
  - [ ] no

## Policy Notes

This task touches:

- [ ] authentication/authorization
- [ ] database/migrations
- [ ] dependencies
- [ ] public API
- [ ] deployment/config
- [ ] security/privacy
- [ ] generated files

Required approval:

- [ ] yes
- [ ] no

Reason:

## Implementation Notes

Record discoveries and important choices while working.

## Test Requirements

Expected checks:

- [ ] unit tests
- [ ] integration tests
- [ ] e2e tests
- [ ] lint
- [ ] build
- [ ] manual verification

## Done Evidence

Fill before review/done:

- Changed files:
- Commands run:
- Test results:
- Behavior verified:
- Known limitations:

## Handoff Notes

Use this if incomplete or risky.

## Links

- GitHub Issue:
- PR:
- Related ADR:
````

### `multiagent/templates/handoff-template.md`

````md
---
task: GH-000
status: blocked
from_agent:
to_agent: next
created_at: YYYY-MM-DDTHH:MM:SSZ
branch:
---

# Handoff: GH-000

## Current Status

Explain exactly where the work stands.

## What Changed

- Changed file/path:
- Changed file/path:

## What Remains

- [ ] Remaining step 1
- [ ] Remaining step 2

## Blockers

Describe what blocked progress.

## Commands Run

```bash
<command>
```

Result:

```text
<summary>
```

## Important Context

Record anything the next agent should not have to rediscover.

## Risks

- Risk 1
- Risk 2

## Recommended Next Step

State the next concrete action.
````

### `multiagent/templates/changelog-entry-template.md`

````md
YYYY-MM-DD | GH-000 | status | one-line summary | agent-name | branch-or-pr

Example:

```md
2026-08-24 | GH-123 | review | Added empty-password login validation and regression test | codex | agent/GH-123-login-validation
```
````

### `multiagent/templates/adr-template.md`

````md
# ADR-0000: Decision Title

Date: YYYY-MM-DD

## Status

Proposed / Accepted / Superseded

## Context

What problem or tradeoff led to this decision?

## Decision

What did we decide?

## Consequences

Positive:

- Item

Negative:

- Item

## Alternatives Considered

- Alternative 1
- Alternative 2
````

### `multiagent/templates/requirements-breakdown-template.md`

````md
---
source_issue:
triage_outcome: agent:needs-breakdown
triaged_by:
created_at: YYYY-MM-DD
updated_at: YYYY-MM-DD
---

# Requirements Breakdown

## Source Issue

- Issue:
- Title:
- Link:

## Requirement Summary

Summarize the requested outcome in plain language.

## Issue Points

```text
1 issue point = 1 hour of expected implementation, verification, and documentation work
```

Issues over 8 issue points should be split into smaller issues before coding.

## Readiness Check

- [ ] clear goal
- [ ] clear acceptance criteria
- [ ] enough context to begin
- [ ] test or verification expectation
- [ ] reasonable scope for one PR
- [ ] estimated at 8 issue points or less
- [ ] no unresolved product decision
- [ ] dependencies are known

Issue point estimate:

- Parent estimate:
- Split required because estimate is over 8 issue points: yes/no

## Ambiguities / Questions

- Question 1:
- Question 2:

## Proposed Sub-Issues

### 1. Sub-Issue Title

Goal:

Acceptance criteria:

- [ ] Criterion 1
- [ ] Criterion 2

Dependencies:

- Depends on:
- Blocks:

Labels:

- `agent:ready`
- `priority:P2`
- `type:feature`
- `issue-points:1`

Issue points:

- 1

Verification:

- Expected command or manual check:

Sequence:

- 1

## Parent Issue Updates

- [ ] Add `agent:split`
- [ ] Remove `agent:ready`
- [ ] Link all child issues
- [ ] Add progress checklist to parent
- [ ] Leave parent open until child issues are done
````

### `.github/ISSUE_TEMPLATE/agent_task.yml`

````yaml
name: Agent Task
description: Create an implementation-ready task for an agent.
title: "[Task]: "
labels:
  - agent:needs-triage
body:
  - type: markdown
    attributes:
      value: |
        Use this template for work intended to fit in one focused PR. An agent will triage the issue before implementation and move it to `agent:ready` only when it has clear scope, verification, and an estimate of 8 issue points or less.

        1 issue point = 1 hour of expected implementation, verification, and documentation work.
  - type: textarea
    id: goal
    attributes:
      label: Goal
      description: What outcome should this task achieve?
      placeholder: Describe the concrete result.
    validations:
      required: true
  - type: textarea
    id: context
    attributes:
      label: Context
      description: Provide background, links, examples, user reports, or constraints.
    validations:
      required: true
  - type: textarea
    id: acceptance_criteria
    attributes:
      label: Acceptance Criteria
      description: List observable conditions that must be true for this task to be complete.
      placeholder: |
        - [ ] ...
        - [ ] ...
    validations:
      required: true
  - type: textarea
    id: affected_area
    attributes:
      label: Affected Area
      description: Which files, modules, workflows, APIs, or docs are likely involved?
    validations:
      required: true
  - type: textarea
    id: expected_verification
    attributes:
      label: Expected Verification
      description: What tests, commands, or manual checks should prove the work is done?
      placeholder: |
        - [TEST_COMMAND]
        - Manual check:
    validations:
      required: true
  - type: dropdown
    id: priority
    attributes:
      label: Priority
      options:
        - priority:P0
        - priority:P1
        - priority:P2
        - priority:P3
      default: 2
    validations:
      required: true
  - type: dropdown
    id: type
    attributes:
      label: Type
      options:
        - type:feature
        - type:bug
        - type:research
        - type:refactor
        - type:docs
        - type:test
        - type:chore
      default: 0
    validations:
      required: true
  - type: dropdown
    id: issue_points
    attributes:
      label: Issue Points
      description: Estimate total implementation, verification, and documentation effort. Anything over 8 issue points should be broken into sub-issues.
      options:
        - 1 issue point
        - 2 issue points
        - 3 issue points
        - 4 issue points
        - 5 issue points
        - 6 issue points
        - 7 issue points
        - 8 issue points
        - Over 8 issue points - needs breakdown
      default: 0
    validations:
      required: true
  - type: textarea
    id: dependencies
    attributes:
      label: Dependencies
      description: List prerequisite issues, decisions, approvals, services, credentials, or access needs.
      placeholder: |
        - None known
    validations:
      required: true
  - type: textarea
    id: security_data_impact
    attributes:
      label: Security / Data Impact
      description: Note any impact on auth, authorization, persistence, secrets, billing, or user data.
      placeholder: |
        - No security or data impact expected
    validations:
      required: true
  - type: textarea
    id: additional_notes
    attributes:
      label: Additional Notes
      description: Anything else the triage or implementation agent should know.
    validations:
      required: false
````

### `.github/ISSUE_TEMPLATE/requirements_epic.yml`

````yaml
name: Requirements Epic
description: Capture a larger requirement that agents should triage and break down.
title: "[Epic]: "
labels:
  - agent:needs-triage
body:
  - type: markdown
    attributes:
      value: |
        Use this template for larger requirements, multi-area changes, or work that may need several child issues. A triage agent should classify it before implementation and split it when appropriate.

        1 issue point = 1 hour of expected implementation, verification, and documentation work. Requirements over 8 issue points should be broken into smaller issues.
  - type: textarea
    id: requirement_summary
    attributes:
      label: Requirement Summary
      description: Summarize the requirement in plain language.
    validations:
      required: true
  - type: textarea
    id: user_business_outcome
    attributes:
      label: User / Business Outcome
      description: What user or business result should this enable?
    validations:
      required: true
  - type: textarea
    id: known_constraints
    attributes:
      label: Known Constraints
      description: List technical, product, timing, compliance, security, or operational constraints.
    validations:
      required: true
  - type: textarea
    id: proposed_scope
    attributes:
      label: Proposed Scope
      description: What should be included?
    validations:
      required: true
  - type: textarea
    id: non_goals
    attributes:
      label: Non-Goals
      description: What should explicitly stay out of scope?
    validations:
      required: true
  - type: textarea
    id: acceptance_criteria
    attributes:
      label: Acceptance Criteria
      description: List overall completion criteria for the requirement.
      placeholder: |
        - [ ] ...
        - [ ] ...
    validations:
      required: true
  - type: textarea
    id: possible_sub_areas
    attributes:
      label: Possible Sub-Areas
      description: Which areas might become child issues?
      placeholder: |
        - API
        - UI
        - tests
        - docs
    validations:
      required: false
  - type: dropdown
    id: estimated_issue_points
    attributes:
      label: Estimated Issue Points
      description: Estimate total work if known. Anything over 8 issue points should be split into child issues.
      options:
        - Unknown
        - 1 issue point
        - 2 issue points
        - 3 issue points
        - 4 issue points
        - 5 issue points
        - 6 issue points
        - 7 issue points
        - 8 issue points
        - Over 8 issue points - needs breakdown
      default: 0
    validations:
      required: true
  - type: dropdown
    id: priority
    attributes:
      label: Priority
      options:
        - priority:P0
        - priority:P1
        - priority:P2
        - priority:P3
      default: 2
    validations:
      required: true
  - type: input
    id: deadline
    attributes:
      label: Deadline If Any
      description: Use a concrete date if there is a deadline.
      placeholder: "YYYY-MM-DD or none"
    validations:
      required: false
  - type: textarea
    id: open_questions
    attributes:
      label: Open Questions
      description: What still needs product, design, security, data, or technical clarification?
    validations:
      required: false
````

## Final Setup Checklist

After creating the files:

- [ ] Project-specific placeholders are filled.
- [ ] Existing docs were merged, not blindly replaced.
- [ ] GitHub labels exist.
- [ ] Issue templates parse as YAML.
- [ ] `AGENTS.md` points to `docs/agentic-workflow.md`.
- [ ] `docs/agentic-workflow.md` tells agents where to read and when.
- [ ] `multiagent/protocol.md` defines triage and lifecycle.
- [ ] `multiagent/policies/decomposition.md` defines issue points and split rules.
- [ ] `multiagent/templates/` has task, handoff, changelog, ADR, and breakdown templates.
- [ ] No product feature implementation was included in the setup commit.
