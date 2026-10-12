---
record_uid: ""
id: TASK-000
aliases: []
requirement_keys: []
source_references: []
record_role: authoritative
source: local
source_url:
title: ""
kind: implementation
status: backlog
outcome:
priority: P2
type: feature
sequence: 0
issue_points:
tracking_parent:
parent:
implementation_items: []
execution_children: []
depends_on: []
claimed_by:
claim_token:
claimed_at:
last_checkpoint:
affected_areas: []
branch:
worktree:
pr:
created_at:
updated_at:
imported_at:
migration_id:
---

# Task Title

Use for Local work records; in GitHub mode use these content sections in issue descriptions. Supplemental local notes must set `record_role: supplemental` and link their authoritative record. Select status and relationships using the tracking, task-status, and decomposition policies.

Generate a stable unique `record_uid` for new work. Preserve it, source identities, and aliases across migration. `outcome` distinguishes completed, cancelled, duplicate, or unknown historical results. Do not treat this example as a ready task.

## Goal And Context

Describe the outcome, background, and original requirement. Preserve user-authored acceptance criteria.

## Acceptance Criteria

- [ ] Observable condition

## Research Summary

- Source document sections/revisions and stable requirement keys:
- Requirement classification and scope authorization:
- Existing implementation and duplicate task checks:

- Files, task history/comments, docs, and tests inspected:
- Findings and likely root cause:
- Dependencies and risks:
- Unknowns and decisions required:
- Verification expectation:
- Estimate and decomposition decision:

## Linked Work

- Tracking parent or execution parent:
- Independent implementation items:
- Execution children and reciprocal relationships:
- Dependencies, sequence, and status:
- Parent summary of findings, fixes, blockers, and remaining work:

## Implementation Notes

Record discoveries, design decisions, fixes, scope changes, and changed files as work progresses.

## Permissions

- Sensitive areas or public contracts affected:
- Required approval and existing authorization:
- Justification for shared/configuration changes:

## Ownership And Handoff

- Owner / claim token / timestamp / last checkpoint:
- Branch / worktree / PR:
- Overlapping work and coordination:
- Blockers / remaining work / next safe action:
- Release or transfer evidence:

## Verification And Acceptance

- Acceptance criteria evidence:
- Actual commands and results:
- Skipped checks, reason, residual risk, and reviewer acceptance:
- Parent/child descriptions updated:
- Review evidence and PR:
- Verified merge or explicit acceptance:
- Outcome and remaining limitations:

## History

Append actual status events using `multiagent/templates/changelog-entry-template.md`. Preserve prior entries. In Local mode this is the durable outbox for tracked monthly logs. Record export delivery separately by event ID after its maintenance PR merges. Imports retain original provenance; do not fabricate past transitions.

## Links And Provenance

- Original record and aliases:
- PRs, related docs, and decisions:
- Migration ID, original timestamps, and import limitations:
