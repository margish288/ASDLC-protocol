# Ownership And Recovery

One active owner per implementation item. A tracking parent may have a coordinator while different agents own its independent children.

## Claim Before Editing

Record owner, claim token, claim time, last checkpoint, work branch, worktree path, affected areas, and planned next action in the selected tracker. Use UTC timestamps. Re-read status, dependencies, existing claims, and overlapping work before claiming. Only ready, unblocked implementation work can be claimed.

- Local, same-machine work: acquire an exclusive lock in the configured state store before allocating task IDs or updating a claim. Use an atomic lock primitive; a read followed by a write is not a lock. Release it after the update.
- GitHub work: record the claim in the issue and re-read it before editing. Labels, assignments, and comments are not an atomic lock. For concurrent agents, designate one dispatcher to serialize claims, or use an existing shared locking service. Without one, limit claiming to one agent at a time.
- Distributed Local mode: tracked files alone do not serialize claims. A shared coordinator/locking mechanism must be configured before enabling concurrent writers. Ignored files in separate clones cannot coordinate ownership.

When another owner is present or claims race, stop the conflicting implementation and coordinate; do not choose a winner by silently overwriting the claim.

## Work Isolation

Use a separate worktree and approved branch for each concurrently implemented independent item. Check both code-area overlap and shared configuration/test changes. Coordinate overlapping files before editing. A clean merge is not proof that behavior is compatible; run integration checks after combining related changes.

Execution sub-issues sharing one PR may use the parent's work branch when worked sequentially by one owner. Record that association rather than creating competing branches with the same numeric name.

## Checkpoints And Recovery

Update the checkpoint at meaningful transitions, before stopping, and when scope changes; do not add monthly logs for routine heartbeats. Include actual commands/results and remaining work.

Configure a stale-claim interval during setup. An expired checkpoint triggers investigation, not automatic ownership theft. Inspect the branch, PR, worktree, and tracker, then obtain a handoff or coordinator decision before reclaiming. Never reset or delete another owner's uncommitted work.

Release ownership on completion, cancellation, or an accepted handoff. Leave durable handoff context using `multiagent/templates/handoff-template.md`, including the claim transfer and next safe action.
