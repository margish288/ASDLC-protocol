# Work Log: YYYY-MM

Append new status-event entries only. Never edit, replace, collapse, delete, or rewrite earlier entries for the same issue or task. If later details become available, append another line.

In local-only installs, keep this file ignored under `.agent-protocol/` and do not commit or push it. In explicit tracked-log installs, when a status event happens during branch work, add the matching log line before committing and include this file in the same commit/PR as the related work or status change. Do not push completed work and then create a separate log-only follow-up commit for the matching status event.

Format:

```text
YYYY-MM-DD | task | status | summary | agent | branch/pr
```

## Entries

YYYY-MM-DD | GH-000 | agent:ready | Issue researched and ready for implementation | agent-name | feature/000
YYYY-MM-DD | GH-000 | agent:in-progress | Claimed issue and started implementation | agent-name | feature/000
YYYY-MM-DD | GH-000 | agent:review | Opened PR with implementation and verification evidence | agent-name | PR #000
YYYY-MM-DD | GH-000 | agent:done | PR merged and issue completed | agent-name | PR #000 / commit
