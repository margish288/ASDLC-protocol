# Agentic Development Protocol

This is the runtime workflow for a target repository. Read the installed `installation.json` and `project/context.md` first. Paths in this document are relative to the protocol root unless marked as target-repository paths.

## Canonical Policies

| Concern | Authority |
| --- | --- |
| Documentation discovery and task creation | [document-intake](policies/document-intake.md) |
| Ignored ASDLC files versus product deliverables | [storage](policies/storage.md) |
| Tracker choice, records, and identifiers | [tracking](policies/tracking.md) |
| Tracker switching and history | [migration](policies/migration.md) |
| Research, estimates, implementation issues, sub-issues | [decomposition](policies/decomposition.md) |
| Status transitions, review, and completion | [task-status](policies/task-status.md) |
| Claims, concurrent work, and recovery | [ownership](policies/ownership.md) |
| Branch naming, commits, and PRs | [git](policies/git.md) |
| Monthly append-only status history | [logging](policies/logging.md) |
| Permissions and approvals | [permissions](policies/permissions.md) |
| Verification evidence | [testing](policies/testing.md) |
| Secrets and sensitive behavior | [security](policies/security.md) |
| Dependency changes | [dependencies](policies/dependencies.md) |
| Server-side protections and CI | [enforcement](policies/enforcement.md) |

Installation and upgrades are governed by `docs/setup.md`. If policies conflict, stop the affected action and report the conflict; do not choose whichever rule permits more access. Source template maintenance is governed by the source repository's `AGENTS.md`.

## Work Cycle

When the user starts from documentation rather than an existing task, run the document-intake policy first: discover relevant sources and existing work, research gaps, reconcile tasks and execution children in the selected tracker, then continue this cycle. The user does not need to translate documents into issues or request each intermediate step. Complete any missing initial setup and tracker selection before creating work records.

1. Confirm the target repository, working tree, installation revision, selected tracker, and existing claims. Refresh parent-branch information when access permits, without overwriting local work.
2. Work on the user's assigned task. When asked to choose, select unblocked work by P0, P1, P2, P3, then dependency/sequence order and oldest ready record. Never substitute a different task silently.
3. Research the active record, code, tests, docs, dependencies, risks, and acceptance criteria. Write findings and the estimate into its description before creating a breakdown or coding.
4. Classify and decompose using the decomposition policy. Resolve ambiguity or record a blocker. Only ready implementation items of eight issue points or less can be claimed.
5. Claim the task using the ownership policy and create or resume its approved work branch. Record actual status transitions using the logging policy.
6. Implement the scoped work. Update findings, fixes, changed files, parent summaries, and verification evidence in the selected tracker. Re-triage materially changed scope.
7. Run relevant checks. For tracked logs, include the status events already known in the related work commit. Never fabricate a PR number, merge result, or future status.
8. Push the approved work branch and open a PR when code changed. Move the record to review only when the task-status review gates pass.
9. After verified merge or explicit acceptance, complete children before parents. Record completion and post-merge history using the configured logging path.
10. Release ownership on completion or handoff. Record blockers and remaining work before stopping.

Local and GitHub tracking follow this same cycle. Tracker selection does not waive PR-only changes, verification, or permission boundaries. An unavailable tracker is a blocker, not permission to create a second authoritative tracker.
