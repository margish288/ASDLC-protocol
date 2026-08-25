# Work Logs

In a target repository, keep one-line chronological task entries here. Work logs are append-only.

In this protocol-template repository, do not create real monthly work log files. Keep only this README and reusable monthly templates such as `YYYY-MM.md`.

Agents must add a new line for every meaningful issue/task event and status transition. Do not update, replace, collapse, delete, or rewrite any previous log entry for the same issue or task.

If later information becomes available, such as a PR number, merge commit, blocker resolution, or done status, append another line with that information instead of editing the earlier line.

Multiple entries for the same issue or task are expected. The log should show the full timeline, such as:

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
