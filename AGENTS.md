# Agent Protocol Template Instructions

This repository is the source of a reusable agent workflow, not an installed product workspace. Keep only policies, documentation, templates, and clearly marked examples. Do not create live tasks, monthly logs, handoffs, installation manifests, or migration records here.

## Read Order

Before changing the template, read:

1. This file.
2. `docs/agentic-workflow.md`.
3. `docs/project-overview.md`.
4. `docs/setup.md`.
5. `docs/testing.md` and `docs/conventions.md`.
6. `multiagent/protocol.md` and `multiagent/policies/permissions.md`.
7. The canonical policies affected by the change.

GitHub issue tracking and local task creation described by the runtime protocol apply to target repositories. Do not initialize either tracker just to maintain this template.

## Maintenance Rules

- Inspect the working tree and preserve existing user changes.
- Keep each rule in its canonical policy. Entry points and setup prompts reference policies instead of embedding copies.
- Keep Local and GitHub modes consistent in research, decomposition, evidence, and completion requirements.
- Update related templates and adapters when a contract changes.
- Follow `multiagent/policies/git.md` for branch naming and PR-only changes. Never commit or push directly to a parent branch.
- Run the checks and scenario review in `docs/testing.md` before finishing.
- Explain changed behavior, verification, and any limitations.

## Installation Boundary

Do not copy this maintenance file as the target repository's runtime instructions. Use `multiagent/templates/target-agents-template.md` to create `.agent-protocol/AGENTS.md` during installation. The source and target repositories have different responsibilities.

`docs/setup.md` is the installation authority. The runtime workflow and its policy map live in `multiagent/protocol.md`.
