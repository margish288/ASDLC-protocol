# Monthly Status Log Policy

Logs are repository-level monthly audit history, supplemental to the selected tracker. Configure storage independently in `installation.json`. Use the UTC month of the actual event: `<YYYY-MM>.md`.

## Append Only

Append a new line for each meaningful status transition, including ready, in-progress, blocked, review, done, cancellation, and reopening. Use the active tracker's status spelling. Do not log routine chatter or checkpoints without a status change.

Never edit, replace, collapse, reorder, or delete previous entries. Corrections and late details are new entries referencing the original event ID. Repeated task IDs are expected. When resolving merge conflicts, preserve both agents' entries and their original contents.

Every event has a stable unique event ID, UTC timestamp, task identity, status, summary, actor, and evidence reference. Retrying delivery of the same event must not duplicate it: check the event ID first. A new transition gets a new ID even when the task returns to a previous status.

## Storage Modes

| Mode | Location and behavior |
| --- | --- |
| `local` | Default `.agent-protocol/state/logs/`; ignored, not committed, not shared by Git. Append when the event occurs. |
| `tracked` | Explicit target-repository path outside ignored protocol files, such as `multiagent/logs/`; shared through PRs. |

Do not force-add ignored logs. Installing the protocol locally does not imply permission to create tracked log files. Explain the sharing tradeoff and record the user's choice. Logs from separate ignored clones are not a complete team audit trail.

## Work Commits And Actual Events

For tracked logs, append events already known during branch work before the related commit and include them with that work. Do not push completed work and then make a per-feature follow-up commit just to add its matching log. Never amend history merely to insert a log.

Only record events that happened. If the PR does not yet exist, record the actual in-progress/verification event and branch, not an invented review event or PR number. Once a PR exists, review can be recorded with the next substantive work commit, or delivered through the status-maintenance path below if no further work commit is needed. This avoids both fabricated history and log-only feature commits.

## Events After The Last Work Commit

Tracked logging requires a configured status-maintenance owner, cadence, and PR base before setup can be considered complete:

1. Record the actual review, merge/done, or other late transition immediately in the selected tracker. Include its stable event ID, timestamp, actor, and evidence.
2. The designated human, coordinator, or configured bot collects unexported status events across tasks at the configured cadence. Use a durable event outbox: GitHub comments in GitHub mode; append-only task History sections in Local mode. The outbox must be accessible to that owner.
3. On an approved numbered work branch for a status-maintenance issue/task, append those events to the months in which they occurred and open a batch maintenance PR. Never push directly to a parent branch. This is an explicit batched audit path, not a log-only follow-up for every feature.
4. Mark delivery in the outbox only after the maintenance PR merges. A retry checks event IDs already present and in open maintenance PRs. Do not recursively log audit-export bookkeeping as new product status events.

Completion depends on the task-status gates and the durable event record, not on waiting for a later audit-export PR. Show pending export separately. If no maintenance owner/path is available, report tracked logging incomplete and ask for a supported configuration; do not promise that every future event can appear in an earlier commit.

Local logging appends late events immediately and needs no maintenance PR. Migration imports preserve provenance; they do not synthesize historical transitions. Formats are in `multiagent/logs/YYYY-MM.md` and `multiagent/templates/changelog-entry-template.md`.
