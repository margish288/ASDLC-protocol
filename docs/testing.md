# Testing

## Test Commands

```bash
# all tests
[TEST_COMMAND]

# unit tests
[UNIT_TEST_COMMAND]

# typecheck
[TYPECHECK_COMMAND]

# lint
[LINT_COMMAND]

# build
[BUILD_COMMAND]
```

## When To Run What

- Small isolated change:
- API/backend change:
- UI change:
- Shared logic change:
- Dependency/config change:

## Required Evidence

Agents must record test evidence in the GitHub Issue or PR. Record it in a local task file only when the work falls under an allowed `multiagent/tasks/` exception.

At minimum, include:

- command run
- pass/fail result
- relevant failure summary
- skipped checks and reason
- manual verification notes, when applicable
