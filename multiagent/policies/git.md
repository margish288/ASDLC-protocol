# Git Policy

## Required

- Start from the latest target parent branch unless task says otherwise.
- Use an approved `feature`, `bugfix`, `research`, or `hotfix` branch for every change.
- Keep commits scoped to the task.
- Do not mix unrelated cleanup with feature work.
- Check working tree before and after changes.
- Route all changes through pull requests.

## Parent Branch Protection

Parent branches are any shared integration, release, environment, or deployment branches. This includes `main`, `master`, `dev`, `develop`, `staging`, `qa`, release branches, and any equivalent parent branch regardless of name.

Agents must never commit directly to a parent branch and must never push directly to a parent branch. All changes must start on an approved `feature`, `bugfix`, `research`, or `hotfix` branch and move through pull requests only.

Default promotion flow:

```text
feature|bugfix|research|hotfix branch -> dev -> staging/qa -> main/master
```

If a repository uses different parent branch names, use the same rule: approved work branches feed parent branches only by pull request, and later parent-to-parent promotion also happens only by pull request.

## Branch Names

Branch names must use exactly one of these formats:

```text
feature/<issue-number>
bugfix/<issue-number>
research/<issue-number>
hotfix/<issue-number>
```

Use the active tracker's GitHub Issue number or Local task number for `<issue-number>`. Check the tracking policy's identity map and existing branches to avoid collisions. Preserve an active branch/PR after migration rather than renaming it to a new tracker ID. Sequential execution children may share their implementation parent's branch as recorded by the ownership policy.

Prefix meanings:

- `feature`: new functionality or planned enhancements
- `bugfix`: non-emergency defect fixes
- `research`: investigation, spike, or discovery work
- `hotfix`: urgent production or release-blocking fixes

## Forbidden

Agents must not:

- run `git reset --hard`
- commit directly to `main`, `master`, `dev`, `develop`, `staging`, `qa`, or any other parent branch
- push directly to `main`, `master`, `dev`, `develop`, `staging`, `qa`, or any other parent branch
- locally merge work into a parent branch as a substitute for a pull request
- force push
- rewrite history
- delete branches with unmerged work
- revert user changes unless explicitly instructed

## Commit Messages

Use:

```text
GH-123: short imperative summary
```

For Local tasks:

```text
TASK-000: short imperative summary
```

Use the record's current display ID and retain migration aliases in the task/PR. Docs, tests, refactors, and maintenance use `feature/<number>` for planned changes, `bugfix/<number>` for defects, or `research/<number>` for investigations; do not invent additional prefixes.

Log handling follows `multiagent/policies/logging.md`. Ignored protocol/state files must not be force-added to satisfy a commit rule. Tracked records and code reach parent branches only through PRs. Host/CI protection is defined in `multiagent/policies/enforcement.md`.
