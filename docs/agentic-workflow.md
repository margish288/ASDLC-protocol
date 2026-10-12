# Agent Reading Workflow

## In This Source Repository

Read root `AGENTS.md` for maintenance instructions. Do not initialize target trackers or runtime records. Installation instructions live in `docs/setup.md`.

## In An Installed Target Repository

All protocol paths below are relative to `.agent-protocol/` (the protocol root). Product source paths and configured tracked record paths are relative to the target repository root.

1. Read the target's existing agent instructions, `.agent-protocol/AGENTS.md`, `installation.json`, and `project/context.md`. Confirm the configured tracker and source revision.
2. Read `multiagent/protocol.md` and the tracking, status, permissions, ownership, and storage policies before selecting work. When told documentation is ready and to start working, follow `multiagent/policies/document-intake.md` to discover sources, research gaps, and reconcile tasks before claiming implementation.
3. Read the active record in the selected tracker, related records and comments, affected code, tests, and `multiagent/policies/decomposition.md` before researching or splitting work.
4. Before editing, confirm acceptance criteria, dependencies, ownership, branch, risk, and actual verification commands from `project/context.md`.
5. During work, record findings and changes in the authoritative task description. Keep parent summaries and dependencies current.
6. Before review or completion, read the testing, task-status, and logging policies. Record evidence and actual status events.
7. Before switching trackers, read `multiagent/policies/migration.md`. Before updating the protocol, read `docs/setup.md`.

Use `multiagent/templates/` for record formats. Templates do not override policies. Never execute placeholder commands or infer a tracker choice from which files happen to exist.

If work stops, leave handoff context in the selected tracker, using `multiagent/templates/handoff-template.md`. Another agent must be able to resume without this chat.
