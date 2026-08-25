Append one new line for each meaningful event or status transition. Never edit a previous line for the same issue or task. If later details become available, append another line.

```text
YYYY-MM-DD | GH-000 | status | one-line summary | agent-name | branch-or-pr
```

Example:

```md
YYYY-MM-DD | GH-123 | agent:ready | Issue researched and ready for implementation | agent-name | feature/123
YYYY-MM-DD | GH-123 | agent:in-progress | Claimed issue and started implementation | agent-name | feature/123
YYYY-MM-DD | GH-123 | agent:review | Opened PR with implementation and verification evidence | agent-name | PR #456
YYYY-MM-DD | GH-123 | agent:done | PR merged and issue completed | agent-name | PR #456 / commit
```
