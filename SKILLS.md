# Project Skills

This file describes the project-specific knowledge and capabilities agents should develop while working here.

## Required Project Knowledge

Agents working on this repo should understand:

- `[PROJECT_ARCHITECTURE]`
- `[LOCAL_SETUP]`
- `[TEST_COMMANDS]`
- `[CODE_CONVENTIONS]`
- `[DEPLOYMENT_FLOW_OR_UNKNOWN]`
- GitHub Issue workflow and task handoff protocol
- Requirement triage and decomposition protocol

## Common Work Types

### Feature Work

Expected agent behavior:

- read related files first
- implement only scoped behavior
- add or update tests
- update docs if behavior changes
- preserve existing API/contract shapes unless the task explicitly says otherwise
- provide done evidence

### Bug Fixes

Expected agent behavior:

- reproduce or reason about the bug
- identify root cause
- add regression test where practical
- keep fix minimal
- document changed behavior

### Refactors

Expected agent behavior:

- refactor only inside task scope
- preserve behavior
- run broad enough tests
- avoid mixed feature/refactor commits

### Documentation

Expected agent behavior:

- keep docs factual and current
- avoid speculative claims
- link to relevant files when possible

### Requirement Triage And Decomposition

Expected agent behavior:

- read the full requirement carefully before coding
- identify ambiguity, missing acceptance criteria, and conflicting constraints
- estimate issue points, where 1 issue point = 1 hour
- decide whether the task fits one focused PR and stays at 8 issue points or less
- split requirements over 8 issue points into smaller GitHub issues when work is separable
- give each sub-issue a clear goal, acceptance criteria, dependencies, suggested labels, issue point estimate, verification expectations, and sequence
- sequence dependent work so foundational changes come before UI, integration, or rollout work
- ask for human input when product behavior, data handling, security, payment, or scope boundaries are unclear
- avoid coding until the issue is classified as ready

## Project-Specific Commands

```bash
# Install dependencies
[INSTALL_COMMAND]

# Run development server
[DEV_COMMAND]

# Run tests
[TEST_COMMAND]

# Run typecheck
[TYPECHECK_COMMAND]

# Run lint
[LINT_COMMAND]

# Run build
[BUILD_COMMAND]
```

## Dangerous Areas

Agents need extra care around:

- authentication: `[NOTES]`
- authorization: `[NOTES]`
- database: `[NOTES]`
- migrations: `[NOTES]`
- payment/billing: `[NOTES]`
- deployment: `[NOTES]`
- generated files: `[NOTES]`
- external integrations: `[NOTES]`
- user data/privacy: `[NOTES]`

## Preferred Patterns

- `[PATTERN_1]`
- `[PATTERN_2]`
- `[PATTERN_3]`

## Avoided Patterns

- `[ANTI_PATTERN_1]`
- `[ANTI_PATTERN_2]`
- `[ANTI_PATTERN_3]`
