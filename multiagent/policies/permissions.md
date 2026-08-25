# Agent Permissions Policy

## Green Actions

Agents may do these without approval when scoped to the active task:

- read repository files
- edit source files
- add or update tests
- update documentation
- create approved `feature`, `bugfix`, `research`, or `hotfix` branches
- classify issues for readiness
- create separate implementation issues from a researched oversized parent requirement
- create linked execution sub-issues from a researched ready implementation issue
- update non-terminal GitHub triage labels
- update GitHub Issue bodies and comments
- update PR descriptions and comments
- create or update local task files only for allowed `multiagent/tasks/` exceptions
- append one-line status-event entries to the current monthly work log
- add handoff notes
- run local test/build/lint commands

Green actions do not include editing, replacing, collapsing, deleting, or rewriting previous work log entries.

For local-only installs, monthly work logs stay ignored under `.agent-protocol/` and must not be committed or pushed. For explicit tracked-log installs, green actions do not include pushing completed work and then creating a separate log-only follow-up commit for the matching status event. When the status event happens during branch work, the log entry must be included with the same work commit/PR.

Green actions do not include committing or pushing directly to parent branches. Parent branch changes must follow `multiagent/policies/git.md` and go through pull requests only.

## Yellow Actions

Agents may do these only with written justification in the GitHub Issue or PR. Use a local task file only for an allowed `multiagent/tasks/` exception:

- refactor shared abstractions
- modify config files
- update CI workflows
- change public interfaces
- edit generated files
- add feature flags
- touch security-sensitive code

## Red Actions

Agents must get explicit human approval before:

- adding dependencies
- changing database schema
- writing migrations
- changing auth or permission behavior
- changing billing/payment behavior
- deleting major code paths
- rewriting git history
- changing deployment secrets/config
- closing issues without PR/review

No approval can override the prohibition on direct agent commits or direct agent pushes to parent branches.
