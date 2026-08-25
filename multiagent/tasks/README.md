# Tasks

GitHub Issues are the primary source of truth. Do not create one local task file per GitHub Issue by default.

In local-only installs, this directory lives under `.agent-protocol/multiagent/tasks/` and is ignored. Local task files are private planning or handoff notes unless a human explicitly requests tracked task files.

In this protocol-template repository, do not create live `GH-*` or `TASK-*` files. Keep this directory limited to reusable guidance and template references.

In a target repository, use `multiagent/tasks/` only for:

- repo-only tasks without GitHub Issues
- temporary local planning
- explicit human request
- complex handoff that needs repo-local durable notes

Local task files are supplemental. They must link back to the relevant GitHub Issue or clearly state why no GitHub Issue exists.

Use `multiagent/templates/task-template.md` as the starting point.

## Naming

Explicitly requested GitHub issue task notes:

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
- Keep GitHub Issue body, comments, labels, PRs, and linked sub-issues authoritative.
- Keep status and branch current.
- Record discoveries while working.
- List changed files before review.
- Record commands and results.
- Link the PR when code changes.
- Add handoff notes if incomplete or risky.
