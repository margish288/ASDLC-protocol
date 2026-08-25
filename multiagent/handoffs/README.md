# Handoffs

In a target repository, GitHub Issues and PRs are the authoritative handoff record. Use this directory only for complex handoffs that need repo-local durable notes beyond GitHub or when explicitly requested.

In local-only installs, this directory lives under `.agent-protocol/multiagent/handoffs/` and is ignored. Do not commit or push local-only handoff files.

In this protocol-template repository, do not create live handoff files.

Start from `multiagent/templates/handoff-template.md`.

## Naming

```text
GH-123-short-title-handoff.md
TASK-000-short-title-handoff.md
```

## Required Contents

- current status
- what changed
- what remains
- blockers
- commands run
- important context
- risks
- recommended next step
