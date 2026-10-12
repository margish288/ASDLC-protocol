# Task Records

In Local mode, one task file per work item is authoritative at the configured `tracker.local_path`. Default: `.agent-protocol/state/tasks/` in the target repository. In GitHub mode, do not create task mirrors by default; local notes are supplemental under the tracking policy.

Do not create live tasks in this protocol source repository.

Use `multiagent/templates/task-template.md`. Local files use `TASK-<number>-<short-title>.md`. Allocate IDs under the ownership lock and preserve historical IDs and migration aliases. Supplemental GitHub notes may use `GH-<number>-<short-title>.md` and must identify their authoritative issue.

Local task files contain status, relationships, claim context, research, findings, fixes, verification, and history. Descriptions can evolve; event history is append-only. Keep reciprocal parent/child links current and validate dependencies.

Storage and sharing follow the installation manifest. Ignored files are private to a clone, not automatically available to another agent or backed up by Git. Tracked task records follow PR-only changes.
