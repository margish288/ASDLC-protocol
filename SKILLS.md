# Project Knowledge For Agents

In this source repository, maintain the canonical protocol and reusable templates. In an installed target, use `project/context.md` and linked existing project docs for actual architecture, setup, commands, conventions, and sensitive areas.

## Working Knowledge

Agents should understand:

- the selected tracker and its authoritative records;
- research and decomposition before implementation;
- ownership, worktree isolation, and handoff;
- Git/PR rules and production protections;
- evidence requirements and append-only status history;
- migration identities and versioned protocol updates.

Use the policy map in `multiagent/protocol.md`; this file does not define a second lifecycle.

## Work Types

- Features: inspect related behavior, implement only scoped acceptance criteria, verify, and document evidence.
- Bugs: reproduce or explain the failure, identify the root cause, add meaningful regression coverage where practical, and record the fix.
- Refactors: preserve behavior, stay within scope, and verify affected shared contracts.
- Documentation: keep claims factual, references current, and templates consistent with canonical policies.
- Research: record findings and decisions before proposing implementation items or execution children.
