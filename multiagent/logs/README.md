# Monthly Work Logs

The canonical rules live in [logging policy](../policies/logging.md). Use one repository-level file per UTC month, `<YYYY-MM>.md`, at the manifest's configured log path.

Logs are append-only status history. Multiple entries for one issue/task are expected. Use stable event IDs for retry detection and references to corrections. Do not rewrite prior entries.

Copy the structure, not the illustrative entries, from [the monthly template](YYYY-MM.md). Ignored logs stay local. Explicitly tracked logs accompany related work commits; late events use the configured batch maintenance PR path.

This source repository keeps only this guidance and the reusable template. Do not add live monthly logs here.
