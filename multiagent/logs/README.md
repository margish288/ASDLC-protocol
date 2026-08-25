# Work Logs

In a target repository, keep repo-level monthly work logs here. Work logs are append-only supplemental audit history. They do not replace GitHub as the source of truth.

In the default local-only install, this directory is under `.agent-protocol/multiagent/logs/` and is ignored. Local-only logs are for the current user's agent context and must not be committed or pushed. Shared status belongs in GitHub Issues and PRs.

In an explicit tracked-log install, this directory may be committed at `multiagent/logs/` or another approved tracked path.

In this protocol-template repository, do not create real monthly work log files. Keep only this README and reusable monthly templates such as `YYYY-MM.md`.

Agents must add a new line for every meaningful issue/task status event. Do not log routine progress chatter that does not change or document issue/task status. Do not update, replace, collapse, delete, or rewrite any previous log entry for the same issue or task.

If later information becomes available, such as a PR number, merge commit, blocker resolution, or done status, append another line with that information instead of editing the earlier line.

For local-only installs, append the log entry locally and keep it ignored. For explicit tracked-log installs, when a status event happens during branch work, add the log entry before committing and include it in the same commit/PR as the related work or status change. Do not push completed work and then create a separate log-only follow-up commit for the matching status event.

Multiple entries for the same issue or task are expected. The monthly log should show the full timeline, such as:

```text
YYYY-MM-DD | GH-000 | agent:ready | Issue researched and ready for implementation | agent-name | feature/000
YYYY-MM-DD | GH-000 | agent:in-progress | Claimed issue and started implementation | agent-name | feature/000
YYYY-MM-DD | GH-000 | agent:review | Opened PR with implementation and verification evidence | agent-name | PR #000
YYYY-MM-DD | GH-000 | agent:done | PR merged and issue completed | agent-name | PR #000 / commit
```

Use one file per month:

```text
YYYY-MM.md
```

For example, work done in a given month belongs in:

```text
YYYY-MM.md
```

Copy the format from `multiagent/logs/YYYY-MM.md`.
