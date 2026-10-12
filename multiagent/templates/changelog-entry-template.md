# Status Event Format

Append one new event for an actual status transition. Follow `multiagent/policies/logging.md` for storage, event IDs, retries, work commits, and post-merge delivery.

```text
YYYY-MM-DDTHH:MM:SSZ | unique-event-id | GH-123-or-TASK-042 | actual-status | one-line-summary | agent-name | evidence-reference
```

Use the real UTC timestamp, selected tracker's identity/status, and evidence that already exists. A correction references the original event ID in a new line. Never insert a guessed PR number, future completion, or fabricated imported history.

Tracked events known before a work commit go in that commit. Actual review/done events arising later go into the durable outbox and configured batch maintenance PR when no further work commit is needed. Local logs are appended immediately and remain ignored.
