# Protocol Conventions

## Canonical Rules

Keep operational rules in the relevant `multiagent/policies/` file. Entry points, adapters, and the setup prompt should link to those files instead of embedding alternate copies. Templates describe record shape and refer to the owning policy for behavior.

## Paths And Scope

Protocol paths resolve from the installed `.agent-protocol/` root. Manifest task/log paths and product code paths resolve from the target repository root. Separate source-maintenance instructions from target-runtime instructions.

Project-specific knowledge lives in the installed `project/context.md` or linked project docs. Never replace existing project commands with source template placeholders.

## Format

Use Markdown for human-readable policies and records; use valid JSON for installation settings. Label examples clearly and leave live record sections empty in templates. Use UTC timestamps for status events and migration/update evidence.

Preserve original IDs, timestamps, and provenance when importing records. Do not make sample task numbers look like actual work.

## Changes

When changing a lifecycle contract, update the owning policy, affected templates/adapters, and acceptance scenarios. Update `VERSION` for published protocol changes and keep the installation template version aligned. Do not duplicate full rules in the release/setup prompt.
