# Tracker Migration

- Migration ID:
- Phase: preview / transferring / verifying / active / failed
- Source / destination tracker and repository identity:
- History scope: active-only / active-with-index / full-history
- Approved by / authorization reference:
- Privacy review and authorized remote writes:
- Snapshot/archive location and readability check:
- Coordinator / cutover window / source timestamp:
- Expected counts, filters, and pagination:
- Unavailable data or unsupported history:

## Identity Map

| Stable record UID | Original ID / URL | Destination ID / URL | Existing branch / PR | Verified |
| --- | --- | --- | --- | --- |

Preserve this mapping across retries and future migrations. Remote import markers must identify the stable UID and migration ID so an unknown create result can be found before retrying.

## Completion Index

| Original ID | Title | Original outcome | Completion evidence / date | Historical location |
| --- | --- | --- | --- | --- |

Do not classify cancelled, duplicate, or unknown closed records as completed. Label snapshots as imports; never manufacture historical events.

## Verification And Cutover

- Transferred counts and identity uniqueness:
- Parent links, execution sub-issues, and dependencies verified:
- Findings, acceptance criteria, test evidence, branches, PRs, and claims preserved:
- Source changes since snapshot reconciled:
- Required destination capabilities verified:
- Old records preserved and destination imports non-authoritative until activation:
- Manifest activation time and new tracker:
- Previous tracker marked historical / participating agents informed:
- Pending imports, failure/retry plan, and next action:

## Migration Events

Append timestamped events with a unique event ID, phase, action, actor, and evidence. Preserve prior events during retries.
