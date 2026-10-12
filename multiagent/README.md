# Multiagent Protocol Files

The selected tracker owns the work record: Local task files or GitHub Issues. Read `installation.json` in the installed protocol root to determine which. Never run two authoritative backlogs.

This source repository contains only reusable instructions and examples. Live tasks, logs, claims, handoffs, and migrations belong in target repositories.

## Directory Map

- `protocol.md`: workflow and canonical policy map.
- `policies/`: tracker, lifecycle, migration, ownership, Git, logging, permissions, testing, and enforcement rules.
- `templates/`: copy-ready formats, including installation and migration records.
- `policies/document-intake.md`: discover documentation, research gaps, reconcile tasks, and begin authorized work.
- `policies/storage.md`: keep ASDLC metadata ignored by default while preserving product tracking.
- `tasks/`: task storage guidance; actual target path comes from the manifest.
- `logs/`: monthly log guidance and sample format; actual target path comes from the manifest.
- `handoffs/`: handoff guidance.

Keep durable findings in the authoritative task description, linked PR, or project documentation. Chat alone is not a handoff. Monthly logs summarize status events; they do not replace task evidence.
