# Testing Policy

## Required

Agents must run tests relevant to changed behavior.

At minimum, record:

- command run
- result
- failures
- skipped checks
- reason if a check could not be run

## Test Selection

Use the narrowest meaningful check first, then broader checks when risk is higher.

Examples:

- small utility change: unit test
- API behavior change: unit/integration test
- UI workflow change: component/e2e/manual verification
- shared abstraction change: broader test suite
- config/build change: build command

## Project Commands

Read actual commands from the target's `project/context.md` and repository configuration. Never execute template placeholders. Required CI checks and review gates are configured through the enforcement policy.

## Done Evidence

A task in either tracker cannot move to `review` without verification evidence, following the task-status gates. Record the tested commit or working-tree state so later changes cannot reuse stale evidence.

If tests cannot be run, explain why and mark residual risk.
