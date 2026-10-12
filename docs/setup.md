# Installation And Updates

This is the canonical installer procedure. The user supplies the public protocol repository URL while working in a target repository; the agent fetches and prepares the files. Do not require a manual user clone, and do not initialize this source repository as a target.

Use `multiagent/policies/storage.md` for the boundary between ignored ASDLC files and tracked product deliverables. Installation alone does not authorize product implementation. When the same request also says documentation is ready and to start working, complete setup and then continue through `multiagent/policies/document-intake.md` without requiring another task-creation prompt.

## 1. Inspect And Resolve

- Inspect target Git status, repository root, remotes, existing agent instructions, docs, package manifests, test configuration, CI, and parent branches. Preserve user changes and project instructions.
- Read the source README and this procedure. Resolve the source URL and requested version/ref (default: its default branch) to one exact commit. Read `VERSION` from that commit; fetch all required files from that same commit, not a moving mixture of raw URLs.
- Record the actual source URL, commit, protocol version, and installation time. Network or source failures block installation; never claim a successful fetch without evidence.
- Inspect fetched content before use. Do not execute downloaded scripts as an installation shortcut. Do not copy source `.git/`, live records, credentials, or unrelated files.

## 2. Install Base Files

Default protocol root: `.agent-protocol/` inside the target. Copy these required source files with relative paths preserved:

- `VERSION`
- `docs/`
- `multiagent/protocol.md`, `multiagent/README.md`, `multiagent/policies/`, and `multiagent/templates/`
- `multiagent/tasks/README.md`, `multiagent/logs/README.md`, `multiagent/logs/YYYY-MM.md`, and `multiagent/handoffs/README.md`

Create `.agent-protocol/AGENTS.md` from `multiagent/templates/target-agents-template.md`, not the source repository's maintenance `AGENTS.md`. Create `installation.json` from the installation template using `docs/configuration.md`, and `project/context.md` from the project-context template. These paths are inside the protocol root. Do not copy sample log entries into live monthly files.

For local-only installation, resolve Git's actual exclude location with `git rev-parse --git-path info/exclude`; `.git` can be a file in worktrees. Append `/.agent-protocol/` only if absent. Preserve existing entries. Do not modify tracked `.gitignore` by default. Ignoring does not untrack files already in Git; report that situation and preserve them pending an explicit storage decision. If tracked installation is explicitly selected, resolve any conflicting ignore rule with the user rather than force-adding files.

Default installation is local-only. A tracked protocol installation is opt-in, still under `.agent-protocol/`, and must be delivered through a work branch/PR. Record `protocol_storage` separately from task and log storage.

## 3. Confirm Tracker And Storage

After base files exist, ask: **Use Local tasks or GitHub Issues for this repository?** Explain that GitHub supports shared cross-machine records while ignored Local records belong to this clone. Recommend GitHub for distributed collaboration, but wait for the user's selection.

Persist the choice before initializing its store. Also confirm:

- Local task storage: ignored local files by default; tracked files only by explicit choice. For ignored Local records, record backup/sharing details or explicit acceptance of single-clone use without backup. Tracked Local stores require the coordinator checkout and metadata-maintenance PR procedure described in the tracking policy.
- Monthly log storage: ignored local logs or explicitly tracked shared logs. Explain that ignored logs cannot be in work commits. Tracked logging requires the owner, cadence, PR base, and accessible event outbox in the logging policy.
- Concurrent agents: single writer by default. To enable concurrency, configure a dispatcher or shared lock, independent worktrees, and stale-claim recovery. Do not imply that labels alone lock issues.

Group these choices into a short setup conversation; do not ask again when preferences are already explicit. Leave `setup_status` as `pending` until required choices and validation are complete. Never begin implementation while the tracker choice is unset.

For GitHub mode, verify the intended owner/repository, authentication, Issues availability, read/write capabilities, and sub-issue support. Do not expose credentials in reports. Create/verify labels from `multiagent/policies/task-status.md` only after GitHub mode is chosen and within setup authorization. Preserve existing label meanings; report conflicts. Do not create dummy issues to test access.

For Local mode, initialize the configured task directory and ID allocation/claim mechanism, without dummy tasks. No GitHub Issues, labels, or issue forms are required. PR host access remains a separate requirement for reviewing code.

## 4. Configure Discovery And Project Context

- Preserve any existing target `AGENTS.md`, `CLAUDE.md`, or editor rules. Never replace user instructions with this protocol.
- If root `AGENTS.md` is absent, create it from the local-bootstrap template and exclude `/AGENTS.md` locally. If an untracked file exists, preserve it and propose an additive pointer. Do not overwrite it.
- If root instructions are tracked, add a pointer only if that tracked change is authorized. Otherwise configure an appropriate local agent adapter when supported or require the explicit session instruction: "Before work, read .agent-protocol/AGENTS.md." Add each newly created local-only adapter to Git's local exclude file and verify it is untracked.
- Tool discovery differs. Verify the selected agent can load the instructions, including ignored paths. Do not claim all agents automatically discover a hidden folder. A per-session instruction is a supported fallback and must be recorded in the setup report.
- Record actual architecture, source paths, setup, verification commands, parent branches, PR host, risks, and missing capabilities in `project/context.md`. Reference existing project docs rather than copying them unnecessarily. Unknown values need explicit limitations; never execute placeholders.
- Keep project customizations in `project/`, runtime records in `state/` or configured external locations, and canonical downloaded policies separate. Source maintenance docs are not the target project's setup/test commands.
- Discover references to the user's existing requirements, competitor analyses, specifications, and design documents while inspecting the project. Record their locations in `project/context.md`; leave original project documents in place. Actual document-to-task intake follows the intake policy once work is authorized.
- Inspect production enforcement using `multiagent/policies/enforcement.md`. Apply approved settings where available and report any remaining gaps.
- Install source `.github/ISSUE_TEMPLATE/` files into the target only when the user requests tracked issue forms, on a work branch/PR. They do not function as GitHub forms from an ignored protocol directory.

## 5. Validate And Report

Use `multiagent/templates/setup-report-template.md` and the acceptance scenarios in `docs/testing.md`.

1. Parse `installation.json`. Confirm its schema version, source revision/version, explicit tracker choice, valid storage modes/paths, discovery method, and logging/ownership configuration.
2. Confirm all required policy and template files exist. Verify the installed source-owned files match the resolved source revision; list rendered files and project customizations separately.
3. Prove instruction discovery using the selected tool or the recorded explicit session read. Read the target instructions and project context back.
4. Verify tracker access/capabilities without creating fake work records. For Local storage, check path permissions and backup/sharing choices; for GitHub, inspect repository metadata, issue access, and permissions, reporting unverified write capabilities.
5. Check known project commands against actual manifests/configuration. Run relevant non-destructive checks when available and record pass/fail, skipped checks, and reasons. Do not report missing tools or placeholder commands as passing.
6. For ignored installation paths and every created external bootstrap/adapter, use `git check-ignore -v` and `git ls-files` together: files must be ignored and not already tracked. Include ASDLC versions, manifests, context reports, local task/log/intake state, and any generated `AGENTS.md`, `CLAUDE.md`, or Cursor pointer in this check. Compare `git status --short` to the initial snapshot; preserve unrelated changes. Check explicitly selected tracked task/log paths are outside ignored directories, and product source/tests/docs have not been hidden by broad ignore rules.
7. Confirm configured tracker, storage, branch, logging, and completion instructions agree. Check that an ignored Local store is not advertised as shared across clones.
8. Record actual production enforcement as verified, pending, or unavailable with evidence and responsible owner. A successful local setup does not prove production protection.

Set `setup_status: complete` only when discovery, tracker, storage, and required configuration checks pass. Missing optional tooling may be recorded as a limitation; missing required access keeps setup pending. Keep `enforcement.status` separate so a usable installation is never advertised as production-ready with pending protection.

Report source revision, tracker choice, installed locations, discovery method, ignore rules, tracked changes requested, checks run, limitations, and next required action. Store the report locally in `project/setup-report.md`; do not create a product task or monthly log just for setup unless requested.

If the user also authorized work from documentation, continue with source intake and the first researched ready task after required setup checks pass. Do not end at the setup report or backlog proposal unless the user requested setup/planning only or a real blocker prevents implementation.

## Updates And Reinstallation

1. Read the existing manifest and preserve its choices; do not silently reset the tracker or storage on reinstall.
2. Fetch the requested release/ref into a temporary staging location and resolve its exact commit. Compare old source files, current installed files, and new source files to identify customization conflicts.
3. Show the policy/version changes, compatibility concerns, and planned file changes. Honor existing update authorization; resolve substantive conflicts with the user before replacing custom behavior.
4. Back up the current installation and manifest. Replace only source-owned files; preserve `project/`, `state/`, task history, migration mappings, and project adapters. Merge custom policy changes explicitly rather than overwriting them.
5. Revalidate discovery, tracker configuration, and policy consistency. Update the manifest version/revision only after success. On failure, restore protocol files/configuration from backup without rolling back task history.
6. Record update provenance in the setup report. A protocol update never switches trackers, enables concurrent writers, changes shared repository settings, or migrates data implicitly.

Switching trackers is governed separately by `multiagent/policies/migration.md`.
