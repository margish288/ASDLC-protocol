# Agentic Development Setup Prompt

Give an agent this public repository URL while working inside the target repository. The agent fetches the required files; the user does not need to clone or install the protocol manually.

## Reusable Request

```text
Set up the Agentic SDLC Protocol from this repository:
[PROTOCOL_REPOSITORY_URL]

Inspect the target repository and existing agent instructions first.
Read the source repository's docs/setup.md and follow its installation procedure.
Install protocol files locally under .agent-protocol/ by default, using Git's
local exclude file. Preserve existing project files and instructions.

After installing the base files, ask me whether to use Local tasks or GitHub
Issues before creating any task records, GitHub labels, or issue templates.
Explain how the selected mode stores and shares work. Record my choice and
the exact protocol revision. Do not select a tracker on my behalf.

Use the canonical policies referenced by multiagent/protocol.md; do not
generate alternate copies of their rules. Configure project context, logging,
agent discovery, and verification using docs/setup.md. Show any production
enforcement gaps. Validate setup before reporting it complete.

For a setup-only request, do not implement product features. If I also ask
to start working from existing documentation, complete setup and continue
through multiagent/policies/document-intake.md: discover relevant documents,
research the repository, reconcile tasks/sub-tasks, and implement ready work
within the authorized scope. Keep ASDLC setup and runtime files ignored
under multiagent/policies/storage.md; track normal product deliverables.
```

## Canonical Instructions

- Installation, updates, and validation: [docs/setup.md](docs/setup.md)
- Runtime workflow: [multiagent/protocol.md](multiagent/protocol.md)
- Documentation to tasks and implementation: [document intake](multiagent/policies/document-intake.md)
- Ignored setup files and tracked deliverables: [storage policy](multiagent/policies/storage.md)
- Tracker selection: [tracking policy](multiagent/policies/tracking.md)
- Switching trackers: [migration policy](multiagent/policies/migration.md)
- Shared protection and checks: [enforcement policy](multiagent/policies/enforcement.md)

This prompt intentionally contains no embedded policy or template copies. Fetch the files from one resolved source revision so an installation cannot mix incompatible versions.
