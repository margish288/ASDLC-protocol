# Agent Protocol Template Instructions

This repository is the agentic development protocol template. It defines reusable rules, policies, and file templates that agents copy into or follow inside a target repository.

Do not treat this repository itself as a target product repository. When editing this protocol template, do not create live task files in `multiagent/tasks/`, live monthly work logs in `multiagent/logs/`, handoffs, or other runtime work records. Those files are created only inside a target repository that has installed this protocol.

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

## Template Summary

Template name: Agentic SDLC Protocol

One-line purpose:

> Reusable Markdown protocol and templates that teach coding agents how to research, decompose, document, implement, verify, and hand off work in a target repository.

Primary contents:

- Language: Markdown
- Policies: `multiagent/policies/`
- Templates: `multiagent/templates/`
- Target repo task examples: `multiagent/tasks/README.md`
- Target repo log examples: `multiagent/logs/README.md` and `multiagent/logs/YYYY-MM.md`

## Project Setup Notes

This protocol must be tailored to the target repository when installed. Replace placeholders in the target repository copy:

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

Agents must research and classify issues before coding.

Valid classifications:

- ready to implement
- needs clarification
- needs breakdown
- blocked

Use issue points for estimation:

```text
1 issue point = 1 hour of expected implementation, verification, and documentation work
```

Agents must not implement vague, oversized, or conflicting requirements. Research must happen before implementation, issue splitting, or sub-issue creation. Research includes reading the issue or task, relevant repo docs, affected code, tests, dependencies, and prior local task context when available.

After research, agents must record a concise research summary in the parent issue description or repo-local task file.

An issue estimated over 8 issue points is oversized. Oversized issues must be divided into multiple separate implementation issues before implementation, not into execution sub-issues. Each implementation issue must be estimated at 8 issue points or less, linked from the parent issue, and worked independently.

For a ready implementation issue estimated at 8 issue points or less, agents must create linked execution sub-issues when the work has separable steps that should be tracked independently. Sub-issues must be linked to the parent issue using the platform relationship when available and listed in the parent issue description. Each sub-issue must have:

- parent issue link
- clear goal
- acceptance criteria
- dependencies
- research findings
- implementation/fix notes
- suggested labels
- issue point estimate
- verification expectations
- sequence order

Agents must keep the parent issue description updated with linked implementation issues or sub-issues, current status, summaries of findings and fixes, blockers, and remaining work. When GitHub permissions allow, update the issue description/body directly rather than relying only on comments. A parent issue may only be marked done after all linked implementation issues and execution sub-issues are done.

Agents must ask for human input when:

- product behavior is ambiguous
- acceptance criteria conflict
- scope cannot be reduced safely
- security, payment, or data behavior is unclear

Default flow:

1. Pull latest code when network and repository permissions allow.
2. Read required context files.
3. Find the highest-priority issue or task that is ready for triage or implementation.
4. Research the issue or task and record findings in the parent issue description or task file.
5. Classify the requirement using `multiagent/protocol.md`.
6. Ask questions, mark blocked, or split the issue when it is not ready.
7. If the issue is over 8 issue points, create separate linked implementation issues and keep the parent as the tracking issue.
8. Claim only a ready implementation issue estimated at 8 issue points or less.
9. Create linked execution sub-issues when research shows separable implementation steps.
10. Create an approved work branch.
11. Implement only the scoped sub-issue or implementation issue.
12. Run relevant checks.
13. Update issue descriptions and task file, then append a new one-line work log entry with evidence.
14. Open PR or leave handoff.
15. Move task status forward only when linked implementation issues or execution sub-issues are complete.

## Branch Naming

Branch names must use exactly one of these formats:

```text
feature/<issue-number>
bugfix/<issue-number>
research/<issue-number>
hotfix/<issue-number>
```

Use the GitHub Issue number for `<issue-number>`. For repo-local tasks without a GitHub Issue, use the local task number in the same position.

## Parent Branch Protection

Agents must never commit directly to parent branches and must never push directly to parent branches. Parent branches include `main`, `master`, `dev`, `develop`, `staging`, `qa`, release branches, and any other shared integration, release, environment, or deployment branch regardless of name.

All changes must start on an approved `feature`, `bugfix`, `research`, or `hotfix` branch and move through pull requests only. The default promotion flow is:

```text
feature|bugfix|research|hotfix branch -> dev -> staging/qa -> main/master
```

If this repository uses different parent branch names, the same rule applies: approved work branches feed parent branches only by PR, and parent-to-parent promotion also happens only by PR.

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
- parent issue and sub-issue descriptions include findings, fixes, and verification evidence
- all linked implementation issues and execution sub-issues are done before the parent is marked done
- a new append-only entry is added to `multiagent/logs/<YYYY-MM>.md`
- GitHub Issue or task status is updated
- PR is opened if code changed

## Work Log Rules

Work logs are append-only. Agents must add a new log line for every meaningful issue/task event and status transition, including `agent:ready`, `agent:in-progress`, `agent:review`, and `agent:done` for GitHub Issues or `ready`, `in_progress`, `review`, and `done` for repo-local tasks.

Agents must never edit, replace, collapse, delete, or rewrite previous log entries for the same issue or task. Multiple log lines for the same issue or task are expected and required because they preserve the chronological history of the work.

## Forbidden Actions

Agents must not:

- commit or push directly to parent branches such as `main`, `master`, `dev`, `develop`, `staging`, or `qa`
- commit secrets, tokens, `.env` files, private keys, or credentials
- edit, replace, collapse, delete, or rewrite previous work log entries instead of appending a new log line
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
