# Protocol Validation

This repository is a documentation/template source. It has no product build or runtime tests. Target verification commands belong in the installed `project/context.md`, populated from the real target project.

## Source Checks

Before finishing a protocol edit:

- Run `git diff --check`.
- Parse `multiagent/templates/installation-template.json` as JSON and check it against `docs/configuration.md`. Confirm the version matches `VERSION` and tracker selection remains unset in the template.
- Parse issue-form YAML with an available YAML parser; verify field IDs are unique and referenced status/type labels exist in the canonical status policy. Do not install dependencies merely for documentation checks without authorization.
- Check Markdown links and all canonical policy/template paths resolve.
- Inspect entry points, adapters, issue forms, and templates for conflicting rules. The setup prompt must reference policies instead of embedding copies.
- Confirm no live task, log, handoff, manifest, or migration records were created in this source repository.

## Acceptance Scenarios

Review these against the instructions after lifecycle changes. These are policy scenarios, not claims that remote operations were executed.

| Scenario | Required result |
| --- | --- |
| Fresh setup without tracker preference | Base files installed; ask for Local/GitHub; no task records or GitHub labels until selection |
| Documentation ready; implementation requested | Discover sources, research gaps, reconcile tasks/children, then continue ready work without another planning approval |
| Setup-only or planning-only request | No product implementation beyond the requested scope |
| Competitor observation without an approved requirement | Candidate/question recorded; no automatic feature implementation |
| Repeated or interrupted document intake | Stable requirement map reuses existing tasks; uncertain creates checked before retry |
| Updated or conflicting source documents | Affected scope re-researched; history preserved; unresolved decisions surfaced |
| Source document unavailable | Limitation recorded; request location/access only when needed; never invent contents |
| Default metadata and agent adapters | Versions, tasks/logs/intake, CLAUDE and dedicated Cursor pointers ignored; no broad project-directory excludes |
| Existing tracked agent file or source analysis | Preserve tracking and contents; do not untrack it as part of setup |
| Local selection without GitHub Issues access | Local store usable; PR rules still apply; backup/sharing choice explicit |
| GitHub selection | Explicit repository/access verified; no automatic local task mirrors |
| Existing target agent instructions | Preserved; additive discovery or explicit session read verified |
| Ignored installation and tracked logs | Separate paths; protocol remains ignored; tracked logs included with work |
| Already-tracked protocol files | Ignore rules do not claim to untrack them; storage decision required |
| Reinstall or protocol upgrade | Tracker, project customizations, state, and mappings preserved |
| Failed upgrade | Protocol/config restored; task history never rolled back |
| GitHub outage | Blocker recorded; no silent tracker change |
| Either-direction migration | Preview, approval, snapshot, stable map, two-pass links, verification, then activation |
| Interrupted or repeated migration | Source remains authoritative until activation; no duplicate records |
| Round-trip migration | Original records reused via stable identity; active branch/PR preserved |
| Closed cancelled/duplicate history | Original outcome preserved; not marked successful completion |
| Active-only history choice | Unneeded completed records left untouched; required dependencies referenced |
| Parent and children share one PR | Review permitted together; merge verified before children then parent become done |
| Review/done happens after last work commit | Actual event in durable outbox; tracked export batched; no fabricated event |
| Two agents claim overlapping work | Dispatcher/lock or coordinated stop; no silent claim overwrite |
| Tracked Local task completes after feature merge | Coordinator records completion on maintenance branch; metadata exported by PR; no direct parent commit |
| Parent-to-parent promotion PR | Allowed only on configured promotion paths; not rejected for lacking a numbered work-branch name |
| Stale owner | Investigate and hand off; no reset/deletion of uncommitted work |
| Protection unavailable | Installation/enforcement states distinct; never claim production-ready |
| Same event delivery retried | Stable event ID prevents duplicate export; old lines unchanged |

## Target Setup Checks

Follow `docs/setup.md` and record evidence in the setup-report template. Validate manifest choices, source revision, file integrity, discovery, tracker capabilities, real commands, ignore/tracked paths, and enforcement state. No dummy issues or production pushes are needed.

For project implementation, follow `multiagent/policies/testing.md`. Evidence belongs in the selected tracker and linked PR, with commands, results, skipped checks, and limitations. Failed or unavailable checks are never reported as passing.
