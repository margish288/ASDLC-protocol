# Tracker Policy

## Selection And Authority

During setup, after the base protocol is installed but before creating records or GitHub labels, ask the user to choose `local` or `github`. Explain storage and sharing. Persist the answer in `installation.json`; future agents read it instead of asking again. An unset choice means setup is incomplete and implementation cannot start.

Exactly one tracker is authoritative for the repository's active backlog:

- `local`: task files at the configured `tracker.local_path`, with descriptions, relationships, status, evidence, and handoffs. GitHub Issues are optional historical references.
- `github`: issues in the configured `tracker.repository`, including descriptions, labels, comments, parent/sub-issue relationships, and PR links. Use authenticated `gh` operations against this explicit repository; do not assume the fork or upstream automatically.

PRs and Git remain authoritative for code review and merge evidence in both modes. Local mode does not waive PR requirements. Without access to a PR host, implementation may remain on a work branch awaiting review; do not merge directly to a parent branch.

In GitHub mode, do not mirror each issue into a local task file. Supplemental local notes are allowed for temporary planning, an explicit human request, repo-only work without an issue, or a complex durable handoff. Mark them `supplemental`, link the authoritative record where one exists, and never let them override GitHub status. In Local mode, task files are the normal work record, not an exception.

Unavailable GitHub access is a blocker. Do not silently switch tracker, invent a local substitute, or queue remote writes as if they succeeded. A switch requires the migration policy.

## Storage Is Independent

Protocol files default to ignored `.agent-protocol/`. Local tasks default to `.agent-protocol/state/tasks/`, also ignored. With explicit user choice, local task files may instead be tracked at a target-repository path such as `multiagent/tasks/`. Record the storage mode separately from tracker mode.

Ignored records are not shared or backed up by Git. Explain this during setup. Record the backup location or an explicit choice of single-clone use without backup. Never claim distributed coordination is available from ignored files. For distributed work, recommend GitHub tracking; tracked local tasks still need a shared claim coordinator to prevent concurrent edits.

For tracked Local task files, designate one coordinator checkout as the current record store; other branches' copies are snapshots, not competing trackers. Configure its location, access, backup of pending changes, and metadata-maintenance PR owner/base/cadence in project context before enabling this option. After a feature merges, write its verified completion and History event in that store on an approved maintenance branch, then include those metadata updates in the next batch maintenance PR (alongside tracked log export when enabled). Until merge, participating agents must read that coordinator store, including its pending updates. If they cannot, do not claim shared Local tracking is ready. Never commit final task metadata directly to a parent branch.

## Identity And Record Format

- Local tasks use `TASK-<number>`. Allocate numbers from the configured task store under the ownership lock; never reuse a historical number.
- GitHub tasks use `GH-<number>` for display and the full repository plus issue number as identity. The number alone is not globally unique.
- Preserve a stable `record_uid` across migrations, plus aliases and original source links. See the task and migration templates.
- Before allocating a local number, check the migration map and existing local/remote branch names to avoid collisions with GitHub numbers. Do not reuse a branch belonging to another task.
- Migrating an active task preserves its existing branch and PR. New branches follow the active tracker's numeric identifier and the Git policy.

If a required new branch name belongs to unrelated work, coordinate its resolution before proceeding. Do not overwrite it, delete unmerged work, or invent an unapproved naming suffix to escape the collision.

Use `multiagent/templates/task-template.md` for Local tasks and the same content sections for GitHub descriptions. GitHub issue forms are optional intake aids, not an alternative policy source.

Document-driven records retain stable requirement keys and source references under the document-intake policy. Intake maps remain ignored supplemental provenance, not a second tracker. Re-running intake must reuse matching work instead of creating duplicate tasks or child trees.

## Updates And History

Task descriptions are living records and may be updated. Preserve user-authored requirements and concurrent changes: re-read before writing, edit only relevant sections, and resolve conflicts instead of overwriting a stale body.

Monthly status logs and migration events are append-only. Imported snapshots describe their provenance and do not manufacture a chronological history. The logging and migration policies define how to preserve that history.
