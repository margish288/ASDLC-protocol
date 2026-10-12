# Work Log: YYYY-MM

Target template only. Start a live file with an empty Entries section; the examples below are not real events.

Follow `multiagent/policies/logging.md` for append-only behavior, UTC month selection, local/tracked storage, same-work commits, and late-event export. Reference the selected tracker's task identity and use one stable unique ID per event.

## Format

```text
timestamp-UTC | event-id | task | status | summary | agent | branch-or-PR-or-evidence
```

## Examples (Do Not Copy Into Live Entries)

```text
YYYY-MM-DDTHH:MM:SSZ | unique-event-1 | GH-123 | agent:ready | Research and scope verified | agent-name | owner/repo#123
YYYY-MM-DDTHH:MM:SSZ | unique-event-2 | GH-123 | agent:in-progress | Claimed implementation | agent-name | feature/123
YYYY-MM-DDTHH:MM:SSZ | unique-event-3 | GH-123 | agent:review | PR ready with verification | agent-name | PR #456
YYYY-MM-DDTHH:MM:SSZ | unique-event-4 | GH-123 | agent:done | Merge verified | agent-name | PR #456 / merge-SHA
YYYY-MM-DDTHH:MM:SSZ | unique-event-5 | TASK-042 | review | Implementation ready for review | agent-name | PR #457
```

## Entries
