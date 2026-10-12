# Glossary

- **Protocol root:** Installed `.agent-protocol/` directory containing canonical rules, configuration, and templates.
- **Target repository:** Product repository using this protocol; distinct from this template source repository.
- **Tracker:** The chosen authoritative work store, Local files or GitHub Issues.
- **Implementation item:** Independently scoped task/issue, at most eight issue points, linked to a tracking parent when split from larger work.
- **Execution child:** Sub-issue or child task within an implementation item; tracked independently when useful.
- **Issue point:** One hour of expected implementation, verification, and documentation.
- **Record UID:** Stable task identity preserved across tracker changes, separate from Local/GitHub display IDs.
- **Migration map:** Durable correspondence between original and destination records, preventing duplicates on retries and round trips.
- **Completion index:** Compact historical list of completed/cancelled records with original outcomes and evidence.
- **Outbox:** Durable actual status events awaiting export to tracked monthly logs.
- **Handoff:** Evidence, remaining work, ownership transfer, and next action sufficient to continue without chat history.
- **Production enforcement:** Verified host/CI controls; the presence of Markdown rules alone is not enforcement.
