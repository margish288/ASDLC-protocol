# Installation Manifest Contract

Create `installation.json` in the installed protocol root from `multiagent/templates/installation-template.json`. This is target configuration, not a live file in the protocol source repository. The template deliberately has an unset tracker and pending setup.

All task/log paths in this manifest resolve from the target repository root, not from the protocol root. Keep paths inside the repository, except an explicitly documented external backup or claim service. Reject path traversal and paths that would overwrite existing unrelated files. Rendered files and project customization are listed in the setup report.

## Required Fields

| Field | Valid values and completion requirements |
| --- | --- |
| `schema_version` | Integer `1`; unknown versions require a compatible installer, not silent interpretation |
| `setup_status` | `pending` or `complete`; complete only after the setup checks pass |
| `protocol_version` | Exact value from fetched `VERSION` |
| `source_url` | Actual protocol repository URL |
| `source_revision` | Full resolved Git commit ID used for every fetched source file |
| `installed_at` | Actual UTC ISO 8601 installation timestamp |
| `protocol_storage` | `local` (ignored) or explicitly selected `tracked` |
| `tracker.mode` | `null` before selection, then `local` or `github`; never null for complete setup |
| `tracker.repository` | Explicit `owner/repository` in GitHub mode, or `hostname/owner/repository` for another GitHub host; null permitted in Local mode |
| `tracker.local_path` | Target-relative task directory; default `.agent-protocol/state/tasks` |
| `tracker.local_storage` | `local` or explicitly selected `tracked`; applies to Local tasks or supplemental notes |
| `tracker.backup_or_sharing` | Required explanation in Local mode: actual backup/sharing arrangement or explicit single-clone/no-backup choice |
| `logging.storage` | `local` or explicitly selected `tracked` |
| `logging.path` | Target-relative monthly-log directory; tracked paths must be outside ignored protocol files |
| `logging.timezone` | `UTC`, used consistently for timestamps and month boundaries |
| `logging.maintenance_owner` | Nonempty human/agent/bot identity required for tracked logs |
| `logging.maintenance_cadence` | Concrete export schedule or trigger required for tracked logs |
| `logging.maintenance_pr_base` | Actual protected parent branch required for tracked log export PRs |
| `logging.event_outbox` | Accessible durable source of events, required for tracked logs; see logging policy |
| `ownership.mode` | `single-writer` or `coordinated` |
| `ownership.coordinator` | Required dispatcher/shared lock description for coordinated mode |
| `ownership.claim_store` | Location of claims and actual serialization mechanism; required before work starts |
| `ownership.stale_after_hours` | Positive number; default 24; expiration requests investigation, not automatic takeover |
| `discovery.method` | Verified bootstrap, supported tool adapter, or explicit per-session read procedure |
| `discovery.tool` | Selected agent/tool for which discovery was verified |
| `discovery.verified` | Boolean; must be true for complete setup |
| `enforcement.status` | `verified`, `pending`, or `unavailable`; independent from setup status |
| `enforcement.evidence` | Actual inspection results/reference; required for verified enforcement |
| `enforcement.owner` | Responsible maintainer when controls remain pending |
| `last_migration_id` | Null before migration, then ID of the verified activated migration |

Null logging maintenance fields are valid for local logs. A GitHub-mode installation need not initialize a Local task store. Never store authentication tokens in this manifest.

## State Locations

Defaults within the protocol root:

- `project/context.md`: project customization.
- `project/setup-report.md`: verification, provenance, and update evidence.
- `state/tasks/`: Local authoritative records when selected.
- `state/logs/`: ignored monthly history when selected.
- `state/migrations/`: migration maps, snapshots/index references, and append-only migration events.
- `state/handoffs/`: optional durable local handoff notes.
- `state/intake/`: ignored document inventories, provenance, and requirement-to-task maps; supplemental to the selected tracker.

Do not create dummy tasks, sample log events, or empty migrations to fill these locations. Default ignored storage requires a sharing/backup decision before it can support distributed handoff.

If the protocol itself is tracked, independently ignored runtime state must have explicit exclude rules verified by Git. If Local tasks/logs are explicitly tracked, choose non-ignored target paths. Do not use one blanket storage decision to override another.

For tracked Local tasks, `project/context.md` must identify the authoritative coordinator checkout, access to pending metadata updates, backup, and metadata-maintenance PR owner/base/cadence. The tracking policy defines this procedure independently from log storage. Without those details, tracked Local setup remains pending.
