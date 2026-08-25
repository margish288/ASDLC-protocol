# Protocol Template Overview

## What This Repository Provides

This repository provides a reusable agentic development protocol. It is a template made of Markdown instructions, policies, and sample file formats that agents should follow after the protocol is installed into a target repository.

The default target installation is local-only. Agents copy or sync the protocol into `.agent-protocol/`, ignore it through `.git/info/exclude`, and use GitHub Issues and PRs as the shared work record. Tracked installation is opt-in only.

This repository is not itself a target product repository. Do not create live agent task files, monthly work logs, handoffs, or issue records here. Keep only reusable instructions, policies, templates, and clearly marked examples.

## Primary Users

- Humans who want to install disciplined agent workflow rules into a repository.
- Coding agents that need a clear operating protocol for target repository work.

## Main Capabilities

- Defines agent read order and workflow discipline.
- Defines issue research, decomposition, branching, permissions, testing, logging, and handoff rules.
- Provides templates for task files, work logs, requirement breakdowns, handoffs, ADRs, and changelog entries.

## Non-Goals

This repository does not aim to:

- Host live work records for changes made to this protocol template.
- Contain product-specific code, runtime configuration, deployments, or application tests.
- Replace target repository customization after installation.
- Force target repositories to commit protocol Markdown files by default.

## Important External Systems

- GitHub: target repositories use GitHub Issues and PRs as the authoritative work record with this protocol.
- Database: none.
- APIs: none.
- Deployment: none.
- Monitoring: none.

## Current Maintenance Priorities

- Keep instructions reusable and target-repository agnostic.
- Keep examples clearly marked as examples or templates.
- Avoid committing live task/log artifacts from protocol-template maintenance.
- Keep local-only installation instructions clear so target repositories are not cluttered with protocol files.
