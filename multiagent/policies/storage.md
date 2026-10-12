# Target Repository Storage

Default installation keeps every ASDLC setup and runtime file untracked in the target repository. This policy does not apply to this public protocol source repository, whose reusable policies and templates must remain version-controlled.

## Local-Only By Default

Keep protocol rules, templates, `VERSION`, `installation.json`, project setup/context reports, local tasks, monthly logs, intake maps, migration records, claim metadata, and handoffs under `.agent-protocol/`. Exclude `/.agent-protocol/` through Git's local exclude file, resolved with `git rev-parse --git-path info/exclude`.

Do not copy protocol `VERSION`, `SKILLS.md`, `docs/`, `multiagent/`, or setup prompts into the target's root as tracked setup files. Target project documentation is separate from protocol documentation.

When a tool requires an entry point outside that directory, create only the smallest required pointer and ignore that exact newly created file locally. Examples, only when absent and needed:

```text
/AGENTS.md
/CLAUDE.md
/.cursor/rules/agent-protocol.mdc
```

Do not ignore the entire `.cursor/`, `docs/`, or another shared project directory. Preserve existing `AGENTS.md`, `CLAUDE.md`, Cursor rules, and other user files. If an entry point already exists, use a supported local adapter or explicit session read; modifying a tracked entry point requires authorization.

Never force-add protocol files. Do not automatically install tracked issue templates, PR templates, CI workflows, or settings files just because setup guidance provides them. Shared controls require a separately authorized repository change.

## Product Deliverables Stay Tracked

Agent authorship does not determine whether a file is ignored. Product source, tests, migrations, approved configuration, and deliverable documentation follow the target repository's normal tracking and review rules. Existing secrets, generated output, and other project ignore conventions remain applicable.

An intake map or agent handoff is protocol state. A requested product specification, user guide, or architecture decision is project documentation. If a file's purpose is unclear, resolve that classification before changing its tracking behavior. Do not move, hide, or untrack original analysis documents during intake.

GitHub Issues and PRs are remote records, visible according to repository permissions; local ignore rules do not hide them. Ignored Local tasks/logs are not shared or backed up by Git. In the default setup they are never included in work commits.

## Exceptions And Verification

Tracked protocol, task, or log storage remains an explicit opt-in for users who request it. A request to start work or choose GitHub tracking is not that opt-in. Preserve existing storage choices during updates; surface a conflict with a new local-only requirement rather than silently untracking files.

Before declaring setup complete, record each created external bootstrap/adapter path and its ignore rule in the setup report. Verify the protocol directory and every local-only adapter are both ignored (`git check-ignore -v`) and absent from the index (`git ls-files`). Compare status against the initial working tree. Existing tracked files are unaffected by ignore rules and must not be removed from the index automatically.

Before committing product changes, inspect the staged file list for accidental ASDLC setup/runtime files. Stage intended product paths; report any already-staged protocol files without silently changing the user's staging choices.
