# Setup

## Installing This Protocol In A Target Repository

Default install mode is local-only.

Install the protocol under the target repository's `.agent-protocol/` directory and ignore it locally through `.git/info/exclude`. Do not add these paths to tracked `.gitignore` unless a human explicitly asks for a tracked ignore rule.

Local-only target layout:

```text
target-repo/
  AGENTS.md              local bootstrap, only when no tracked AGENTS.md exists
  .agent-protocol/       ignored local protocol copy
  .git/info/exclude      local ignore rules, not committed
```

Recommended local exclude entries when both the protocol directory and root bootstrap are created:

```gitignore
/.agent-protocol/
/AGENTS.md
```

Add `/AGENTS.md` only when the setup creates an untracked local bootstrap file. If the target repository already tracks `AGENTS.md`, do not overwrite it and do not assume `.git/info/exclude` can hide changes to it.

Root bootstrap content:

```md
# Local Agent Bootstrap

Before doing any work in this repository, read:

`.agent-protocol/AGENTS.md`

This file and `.agent-protocol/` are local-only agent protocol files. Do not commit or push them.
```

After setup, `git status --short` must not show `.agent-protocol/` or the local bootstrap. If those files appear, fix `.git/info/exclude` before doing product work.

Tracked protocol installation is opt-in only. Use tracked protocol files, tracked GitHub issue templates, or tracked work logs only when a human explicitly requests them.

## Target Project Setup Template

## Requirements

- Runtime:
- Package manager:
- Database:
- Other services:

## Install

```bash
[INSTALL_COMMAND]
```

## Environment

Required environment variables:

```text
EXAMPLE_ENV=
```

Use `.env.example` if one is added later. Never commit real secrets.

## Run Locally

```bash
[DEV_COMMAND]
```

## Useful Commands

```bash
[TEST_COMMAND]
[TYPECHECK_COMMAND]
[LINT_COMMAND]
[BUILD_COMMAND]
```

## Common Problems

### Problem

Fix:

```bash
[FIX_COMMAND]
```
