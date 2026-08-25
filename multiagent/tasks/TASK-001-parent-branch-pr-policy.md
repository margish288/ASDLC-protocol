---
id: TASK-001
source: local
github_issue:
title: "Add parent branch PR-only agent and branch naming policies"
status: review
priority: P2
sequence: 001
issue_points: 1
depends_on: []
claimed_by: Codex
branch: feature/001
pr:
created_at: 2026-08-24
updated_at: 2026-08-24
---

# TASK-001: Add Parent Branch PR-Only Agent And Branch Naming Policies

## Goal

Make agent rules explicitly forbid direct commits and direct pushes to parent branches.

## Acceptance Criteria

- [x] Existing branching/git policy is updated instead of creating a duplicate policy file.
- [x] Parent branches include `main`, `master`, `dev`, `develop`, `staging`, `qa`, release branches, and equivalent shared branches under any name.
- [x] Policy requires approved work branch changes to move into parent branches by pull request only.
- [x] Policy requires parent-to-parent promotion to happen by pull request only.
- [x] Top-level agent instructions surface the rule for first-read visibility.
- [x] Branch naming policy allows only `feature/<issue-number>`, `bugfix/<issue-number>`, `research/<issue-number>`, and `hotfix/<issue-number>`.

## Context

User requested a rule update so agents never commit or push directly to parent branches, and all changes move from feature branches to `dev` and onward by pull request only. User later requested branch creation names be limited to `feature/<issue-number>`, `bugfix/<issue-number>`, `research/<issue-number>`, and `hotfix/<issue-number>`.

## Affected Areas

- `AGENTS.md`
- `multiagent/policies/git.md`
- `multiagent/policies/permissions.md`
- `multiagent/protocol.md`
- `multiagent/templates/changelog-entry-template.md`
- `multiagent/tasks/TASK-001-parent-branch-pr-policy.md`
- `multiagent/logs/2026-08.md`

## Issue Points

```text
1 issue point = 1 hour
```

- Estimate: 1
- Over 8 issue points:
  - [ ] yes, split before implementation
  - [x] no

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
- [x] no

Reason: Documentation-only policy update requested by the user.

## Implementation Notes

- Found existing `multiagent/policies/git.md`, so updated it instead of adding a separate branching policy file.
- Added a matching top-level rule in `AGENTS.md` for first-read visibility.
- Added a permissions note that approval cannot override the parent branch direct-commit/direct-push prohibition.
- Created the original task branch after escalating Git branch creation because the sandbox has read-only `.git` access.
- Updated branch naming guidance to allow only `feature`, `bugfix`, `research`, and `hotfix` branches keyed by issue number.
- Renamed the active branch to `feature/001` after the branch naming policy was updated.

## Test Requirements

Expected checks:

- [ ] unit tests
- [ ] integration tests
- [ ] e2e tests
- [ ] lint
- [ ] build
- [x] manual verification

## Done Evidence

- Changed files:
  - `AGENTS.md`
  - `multiagent/protocol.md`
  - `multiagent/policies/git.md`
  - `multiagent/policies/permissions.md`
  - `multiagent/templates/changelog-entry-template.md`
  - `multiagent/tasks/TASK-001-parent-branch-pr-policy.md`
  - `multiagent/logs/2026-08.md`
- Commands run:
  - `git status --short --branch`
  - `rg --files -g 'AGENTS.md' -g 'docs/*.md' -g 'multiagent/**/*.md'`
  - `sed -n '1,260p' AGENTS.md`
  - `sed -n '1,260p' docs/agentic-workflow.md`
  - `sed -n '1,240p' docs/project-overview.md`
  - `sed -n '1,240p' docs/setup.md`
  - `sed -n '1,240p' docs/testing.md`
  - `sed -n '1,260p' docs/conventions.md`
  - `sed -n '1,320p' multiagent/protocol.md`
  - `sed -n '1,260p' multiagent/policies/permissions.md`
  - `sed -n '1,260p' multiagent/policies/decomposition.md`
  - `sed -n '1,320p' multiagent/policies/git.md`
  - `sed -n '1,220p' multiagent/tasks/README.md`
  - `sed -n '1,220p' multiagent/logs/README.md`
  - `sed -n '1,260p' multiagent/templates/task-template.md`
  - `sed -n '1,200p' multiagent/logs/YYYY-MM.md`
  - `find multiagent/tasks -maxdepth 1 -type f -name '*.md' -print`
  - `rg -n "branch|branches|parent|direct commit|push|PR|pull request|main|master|dev|staging|qa" AGENTS.md docs multiagent`
  - `git switch -c agent/TASK-001-parent-branch-pr-policy`
  - `git diff --check`
  - `git diff -- AGENTS.md multiagent/policies/git.md multiagent/policies/permissions.md`
  - `sed -n '1,220p' multiagent/tasks/TASK-001-parent-branch-pr-policy.md`
  - `rg -n "Parent Branch Protection|directly to parent|pull requests only|task/feature branch|No approval" AGENTS.md multiagent/policies/git.md multiagent/policies/permissions.md multiagent/tasks/TASK-001-parent-branch-pr-policy.md multiagent/logs/2026-08.md`
  - `rg -n "agent/GH|agent/TASK|Branch format|Branch Names|Branch Naming|Create branch|task branch|feature branch|branch:" AGENTS.md docs multiagent`
  - `git branch -m feature/001`
  - `git branch --show-current`
  - `rg -n "agent/GH|agent/TASK|feature/<issue-number>|bugfix/<issue-number>|research/<issue-number>|hotfix/<issue-number>|feature/123|bugfix/123|research/123|hotfix/123" AGENTS.md multiagent/protocol.md multiagent/policies/git.md multiagent/templates/changelog-entry-template.md`
- Test results: `git diff --check` passed. Manual documentation review confirmed the parent branch protection rule appears in `AGENTS.md`, `multiagent/policies/git.md`, and `multiagent/policies/permissions.md`. Branch naming guidance now uses only the approved branch formats. Current branch is `feature/001`.
- Behavior verified: Policy now forbids direct agent commits and direct agent pushes to parent branches and requires PR-only promotion.
- Known limitations: No automated tests apply to this documentation-only policy change.

## Handoff Notes

None.

## Links

- GitHub Issue:
- PR:
- Related ADR:
