# Agent Protocol Template Instructions

This repository is the agentic development protocol template. It defines reusable rules, policies, and file templates that agents install locally or explicitly track inside a target repository.

Do not treat this repository itself as a target product repository. When editing this protocol template, do not create live task files in `multiagent/tasks/`, live monthly work logs in `multiagent/logs/`, handoffs, or other runtime work records. Those files are created only inside a target repository that has installed this protocol.

## Target Repository Install Modes

Default install mode is local-only.

For local-only installs:

- copy or sync this protocol under `.agent-protocol/` in the target repository
- create a root `AGENTS.md` bootstrap only when the target repository does not already track `AGENTS.md`
- add `/.agent-protocol/` and any local bootstrap files to `.git/info/exclude`
- do not modify tracked `.gitignore` unless a human explicitly requests a tracked ignore rule
- do not commit or push `.agent-protocol/`, local bootstrap files, local task notes, local handoffs, or local work logs

If the target repository already has a tracked `AGENTS.md`, do not overwrite it for local-only setup. The human must either give the agent a global/tool instruction to read `.agent-protocol/AGENTS.md` or explicitly approve a tracked bootstrap change.

Tracked protocol installation is opt-in only. Use it only when a human explicitly wants protocol files, issue templates, logs, or other workflow documents committed to the target repository.

## Protocol Root

In this protocol-template repository, the protocol root is the repository root.

In a target repository local-only install, the protocol root is `.agent-protocol/`.

Resolve protocol paths such as `docs/agentic-workflow.md`, `multiagent/protocol.md`, and `multiagent/logs/YYYY-MM.md` relative to the protocol root. Target product paths are called out separately as target repository paths.

## First Read Order

Before making changes, read these files:

1. root `AGENTS.md` bootstrap when present
2. `<protocol-root>/AGENTS.md`
3. `<protocol-root>/docs/agentic-workflow.md`
4. `<protocol-root>/docs/project-overview.md`
5. `<protocol-root>/docs/setup.md`
6. `<protocol-root>/docs/testing.md`
7. `<protocol-root>/docs/conventions.md`
8. `<protocol-root>/multiagent/protocol.md`
9. `<protocol-root>/multiagent/policies/permissions.md`
10. `<protocol-root>/multiagent/policies/decomposition.md` when triaging or splitting requirements
11. Relevant GitHub Issue via `gh issue view`; read a local task file only when one exists for an approved exception case

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
- Local-only install target: `.agent-protocol/`

## Project Setup Notes

This protocol must be tailored to the target repository when installed. Replace placeholders in the target repository copy:

- `[IMPORTANT_ENTRYPOINT_1]`
- `[IMPORTANT_ENTRYPOINT_2]`
- `[IMPORTANT_DOMAIN_FOLDER]`
- `[IMPORTANT_TEST_FOLDER]`
- `[KNOWN_ABSENCES_OR_LIMITATIONS]`

## Primary Source Of Truth

GitHub is the primary source of truth for target repository work. Agents must use GitHub Issues, issue labels, issue body/description, issue comments, linked sub-issues, PRs, and PR comments as the authoritative work record.

Agents should use `gh` commands to fetch, inspect, claim, update, comment on, and link issues and PRs when GitHub access is available. Agents must not create local task files for every GitHub Issue by default.

If GitHub cannot be reached or the agent cannot update issue bodies, labels, comments, PRs, or linked sub-issues, do not silently substitute local task files. Ask for access, mark the GitHub Issue blocked when possible, or use a local task file only when the work matches an allowed exception.

Use `<protocol-root>/multiagent/tasks/` only for:

- repo-only tasks without GitHub Issues
- temporary local planning
- explicit human request
- complex handoff that needs repo-local durable notes

Local task files are supplemental notes only. They must not replace or override GitHub labels, issue bodies, issue comments, PRs, or linked sub-issues.

## Agent Workflow

Agents must work from a GitHub Issue labeled `agent:ready` unless the work falls under an allowed `multiagent/tasks/` exception.

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

Agents must not implement vague, oversized, or conflicting requirements. Research must happen before implementation, issue splitting, or sub-issue creation. Research includes reading the GitHub Issue body and comments, relevant repo docs, affected code, tests, dependencies, and permitted local task context when available.

After research, agents must record a concise research summary in the parent GitHub Issue description. Use a repo-local task file only for an allowed exception.

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
3. Find the highest-priority GitHub Issue that is ready for triage or implementation.
4. Research the issue and record findings in the parent GitHub Issue description.
5. Classify the requirement using `multiagent/protocol.md`.
6. Ask questions, mark blocked, or split the issue when it is not ready.
7. If the issue is over 8 issue points, create separate linked implementation issues and keep the parent as the tracking issue.
8. Claim only a ready implementation issue estimated at 8 issue points or less.
9. Create linked execution sub-issues when research shows separable implementation steps.
10. Create an approved work branch.
11. Implement only the scoped sub-issue or implementation issue.
12. Run relevant checks.
13. Update GitHub Issue descriptions/comments, PRs, and linked sub-issues, then follow the work log policy for the repository install mode.
14. Open PR or leave handoff.
15. Move GitHub Issue status forward only when linked implementation issues or execution sub-issues are complete.

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

An issue or allowed local task may only be marked `done` or `review` when:

- acceptance criteria are satisfied
- relevant tests/checks were run
- changed files and verification evidence are recorded in the GitHub Issue or PR
- done evidence is written in the GitHub Issue or PR
- parent issue and sub-issue descriptions include findings, fixes, and verification evidence
- all linked implementation issues and execution sub-issues are done before the parent is marked done
- the work log policy is followed for the repository install mode
- GitHub Issue status is updated
- PR is opened if code changed

## Work Log Rules

Work logs are repo-level monthly files under `<protocol-root>/multiagent/logs/<YYYY-MM>.md`. They are append-only supplemental audit history and do not replace GitHub as the source of truth. Agents must add a new log line for every meaningful issue/task status event, including `agent:ready`, `agent:in-progress`, `agent:review`, and `agent:done` for GitHub Issues or `ready`, `in_progress`, `review`, and `done` for repo-local tasks. Do not log routine progress chatter that does not change or document issue/task status.

Agents must never edit, replace, collapse, delete, or rewrite previous log entries for the same issue or task. Multiple log lines for the same issue or task are expected and required because they preserve the chronological history of the work.

For default local-only installs, work logs are ignored local files under `.agent-protocol/`. Append local status-event entries, but do not commit or push them. GitHub Issue labels, issue body updates, comments, PRs, and PR comments remain the shared record between agents.

For explicit tracked-log installs, when a status event happens during work on a branch, the log entry must be added before the related commit and included in the same commit/PR as the work or status change. Agents must not push code and then create a separate follow-up commit only to add the matching work log entry.

## Forbidden Actions

Agents must not:

- commit or push directly to parent branches such as `main`, `master`, `dev`, `develop`, `staging`, or `qa`
- commit secrets, tokens, `.env` files, private keys, or credentials
- edit, replace, collapse, delete, or rewrite previous work log entries instead of appending a new log line
- push completed work and then add the matching work log entry in a separate log-only follow-up commit
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

If work is incomplete, update the GitHub Issue and PR with handoff context. Create a repo-local handoff in `<protocol-root>/multiagent/handoffs/` only for complex handoffs that need durable notes beyond GitHub or when explicitly requested.

The handoff must include:

- current status
- what was changed
- what remains
- blockers
- commands run
- known risks
- recommended next step
