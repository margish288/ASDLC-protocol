# Agentic Development Setup Repository

This repository is a reusable setup source for installing an Agentic SDLC protocol into another project.

It is not meant to be a project-specific protocol installation. Files such as `AGENTS.md`, `SKILLS.md`, `docs/project-overview.md`, `docs/setup.md`, and `docs/testing.md` intentionally keep project detail fields as placeholders so a coding agent can fill them with the target repository's real setup.

Default target repository setup is local-only:

- copy or sync this repository into `.agent-protocol/` inside the target repository
- add `/.agent-protocol/` and any local bootstrap files to the target repository's `.git/info/exclude`
- create a small root `AGENTS.md` bootstrap only when the target repository does not already track `AGENTS.md`
- do not commit protocol files unless the human explicitly requests a tracked installation

## How To Use

1. Open the target repository in a coding agent.
2. Give the agent this repository URL or the contents of `AGENTIC_DEVELOPMENT_SETUP_PROMPT.md`.
3. Ask the agent to inspect the target repo first, then install the protocol locally under `.agent-protocol/`.
4. Verify `git status --short` does not show the local protocol files.

The reusable setup prompt lives in `AGENTIC_DEVELOPMENT_SETUP_PROMPT.md`.
