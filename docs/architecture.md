# Protocol Architecture

## Components

- Source entry point: `README.md` and `AGENTIC_DEVELOPMENT_SETUP_PROMPT.md`.
- Installer procedure: `docs/setup.md`.
- Version and installation choices: `VERSION`, installation manifest, and `docs/configuration.md`.
- Target entry point: rendered `multiagent/templates/target-agents-template.md`.
- Runtime workflow: `multiagent/protocol.md` and canonical policies.
- Record formats: `multiagent/templates/`.
- Project customization: target `project/context.md` and existing project docs.
- Runtime state: target `state/` or explicitly configured external stores.

## Data Flow

The selected tracker receives research, descriptions, relationships, ownership, and evidence. PRs carry code review and merge evidence. Monthly logs append actual status events as a supplemental audit trail.

Migration copies and verifies records before changing tracker authority. Installation updates replace source-owned protocol files while preserving project configuration and runtime state.

Protocol storage, task tracking, and log storage are independent choices. Ignored local files do not provide cross-clone sharing. Shared production controls live in the Git host/CI and are inspected separately from Markdown instructions.

This is an agent-executed protocol, not an installed background service. No automatic migration, synchronization, locking service, or log-export bot is supplied. Setup must identify an actual agent/human/tool responsible for those procedures rather than claiming automation exists.
