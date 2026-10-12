# Agentic SDLC Protocol

A reusable protocol that teaches agents how to research, plan, implement, verify, and hand off repository work. This repository contains templates and policies, not live project tasks.

## Use In Another Repository

1. Open your target repository in an agent.
2. Give it this public repository URL and ask it to follow [the setup prompt](AGENTIC_DEVELOPMENT_SETUP_PROMPT.md).
3. The agent inspects your project and installs the protocol under `.agent-protocol/`, ignored locally by default.
4. Choose **Local tasks** or **GitHub Issues** when asked. Both use the same lifecycle; only one is authoritative at a time.
5. Review the setup report, including instruction discovery, verification commands, storage choices, and production protection gaps.

No manual clone of this protocol is required. The agent needs access to the source URL. Local tracking does not require GitHub Issues access; PR and branch rules still apply to code changes.

## Start From Documentation

After setup, "The documentation is ready; start working" triggers the [document-intake workflow](multiagent/policies/document-intake.md). The agent discovers relevant documents and existing work, researches gaps, creates or reconciles tasks and execution children in the selected tracker, then implements ready work within the authorized scope. No separate task-writing prompt is needed. It asks only for missing setup choices, inaccessible source locations, unresolved decisions, or required permissions.

Competitor observations do not automatically become approved features. Clear authorized requirements proceed; ambiguous recommendations are recorded for clarification without blocking independent approved work.

## Storage And Sharing

Protocol installation, task tracking, and log storage are separate choices. Ignored files belong to one clone and are not shared by Git. For distributed collaboration, use GitHub tracking with locally installed protocol files. Local tracking requires an explicit backup or sharing arrangement when used across machines.

By default all ASDLC setup/runtime files stay ignored: protocol versions, manifests, policies, local tasks/logs, intake maps, and newly created agent pointers such as `CLAUDE.md` or a dedicated Cursor rule. Product code, tests, and deliverable documentation remain tracked. Existing project agent files are preserved. GitHub Issues/PRs remain visible on GitHub; ignore rules only affect local Git files. See [storage policy](multiagent/policies/storage.md).

Monthly status logs are append-only. Tracked logs are included with the related work commit; ignored logs remain local. See [logging policy](multiagent/policies/logging.md).

## Policy Map

- [Setup and versioned updates](docs/setup.md)
- [Agent workflow and canonical policies](multiagent/protocol.md)
- [Tracker selection](multiagent/policies/tracking.md)
- [Tracker migration and history](multiagent/policies/migration.md)
- [Production enforcement](multiagent/policies/enforcement.md)
- [Protocol validation](docs/testing.md)

The installation manifest records a source revision and project choices. Updates preserve project customization and work history. Switching trackers uses a reviewed migration, never an automatic fallback.
