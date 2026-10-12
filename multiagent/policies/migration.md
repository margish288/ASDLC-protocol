# Tracker Migration Policy

Switching trackers is an explicit user decision, never an outage fallback. Use `multiagent/templates/migration-template.md`. The old tracker remains authoritative until verification and activation succeed.

## History Choice

Ask which history scope to migrate:

| Scope | Transfer |
| --- | --- |
| `active-only` | Unfinished work and references or snapshots of dependencies required to understand it |
| `active-with-index` (recommended) | Active work plus a compact completion/cancellation index with original IDs, outcomes, and links |
| `full-history` | All accessible records, relationships, evidence, and available history, with limitations recorded |

Completed work can be left in the previous tracker; ignoring it during migration does not mean deleting it. For Local-to-GitHub moves, keep the completion index in a preserved archive and link it where accessible. Do not create closed GitHub Issues for historical local tasks unless the user selects that behavior. Do not publish private local notes without reviewing the proposed exported content.

Full history is an import of available evidence, not a promise to recreate original authors, timestamps, platform events, or inaccessible attachments. Retain original values as metadata. Never treat every closed issue as done: preserve completed, cancelled/not-planned, duplicate, and unknown outcomes distinctly. Exclude PR objects when enumerating GitHub issues through APIs that return both.

## Migration Procedure

1. Inspect source and destination access, counts, pagination, relationships, active claims, PRs, local task files, and existing migration maps. Include all pages and explicitly selected filters, not just the first CLI result page.
2. Prepare a preview with source/destination, history scope, proposed records, status mapping, privacy review, unsupported data, unresolved dependencies, and archive/backup locations. Obtain approval of this concrete transfer and any remote writes it requires; existing explicit authorization need not be requested again.
3. Coordinate a cutover window: pause claims and writes in the participating agents, snapshot the source, and record source update times. Do not interrupt another agent or overwrite its work without coordination.
4. Assign a migration ID and maintain a durable mapping of `record_uid`, original source ID, destination ID, and verification result. Create records with migration markers. Search for an existing marker before retrying any creation whose outcome is unknown.
5. Transfer records in two passes: first descriptions and identities, then parent/sub-issue links and dependencies using the completed mapping. Separate implementation issues stay separate; execution sub-issues retain their parent relationships. Preserve branches and PRs.
6. Preserve completion evidence, findings, original outcomes, and source links. Mark imported descriptions and history as imports. Never append invented ready/in-progress/review events for old work.
7. Verify counts against the preview, identity uniqueness, required fields, relationship targets, status mapping, and active PR/claim references. Re-check source timestamps; reconcile changes before activation. Record inaccessible or omitted data. Verify the snapshot/backup is readable.
8. Only after successful verification, update the installation manifest's tracker and `last_migration_id`. Mark the previous tracker as historical in the migration record and notify participating agents of the cutover. Add reciprocal pointers where permitted. Do not delete records or close open issues merely because they moved.
9. Append a migration event and retain the map and completion index at `state/migrations/` (or the configured shared archive). Set a coordinator responsible for keeping that map available across clones before distributed work resumes.

## Failure And Retry

On partial failure, keep the source authoritative and mark destination imports provisional. Resume using the same mapping and migration markers; retries must not duplicate records or comments. Release the cutover pause explicitly when safe. Do not roll back by deleting user records.

After activation, returning to the previous tracker is another migration with reconciliation of new work, not a blind restoration of an old snapshot. Preserve historical aliases and mappings so a round trip updates the existing corresponding records.
