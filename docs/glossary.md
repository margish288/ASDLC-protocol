# Glossary

## Agent

An AI coding assistant or automation working in the repository.

## Agentic Development Protocol

The repo-local workflow that defines how agents pick up tasks, record evidence, and hand off work. In local-only installs it lives under `.agent-protocol/`; in explicit tracked installs it may live in root `AGENTS.md` and `multiagent/`.

## Protocol Root

The directory where protocol files are read from. In local-only target installs this is `.agent-protocol/`. In this protocol-template source repository or explicit tracked installs this is the repository root.

## ASDLC

Agentic software development lifecycle. In this repository, the term refers to the protocol and documentation that help agents work safely and durably.

## Issue Point

An estimate where 1 issue point = 1 hour of expected implementation, verification, and documentation work.

## Handoff

A durable note in `<protocol-root>/multiagent/handoffs/` explaining incomplete work so another human or agent can continue without chat history.

## Done Evidence

The changed files, commands, test results, behavior verification, and limitations recorded before moving a task to review or done.

## [PROJECT_TERM]

[Definition]
