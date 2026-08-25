# Multiagent Workflow Template

This directory contains the reusable repo-local operating system for agents.

When this protocol is installed into a target repository, GitHub Issues are the backlog and files in this directory become durable working memory.

In this protocol-template repository, keep only reusable instructions, policies, templates, and clearly marked examples. Do not create live task files, live monthly work logs, or handoff records here.

GitHub Issues may start as `agent:needs-triage`. Agents should research, classify, and, when needed, decompose requirements before implementation.

This workflow estimates work with issue points: 1 issue point = 1 hour of expected implementation, verification, and documentation work. Issues over 8 issue points should be split into separate implementation issues before coding, not into execution sub-issues.

For the agent-perspective read order, use `docs/agentic-workflow.md`.

## Directory Map

```text
multiagent/
  protocol.md              Process agents must follow
  tasks/                   Target repo task README and task-file templates
  logs/                    Target repo log README and monthly log template
  handoffs/                Target repo handoff guidance
  policies/                Permissions, restrictions, and safety rules
  templates/               Copy-ready templates
```

## Requirement Triage

Agents must not blindly implement large or unclear issues.

Before coding, classify each issue as:

- `agent:ready`
- `agent:needs-clarification`
- `agent:needs-breakdown`
- `agent:blocked`
- `agent:split`

If an issue contains separable work or is over 8 issue points, use `multiagent/policies/decomposition.md` and `multiagent/templates/requirements-breakdown-template.md` to propose implementation issues or execution sub-issues with acceptance criteria, dependencies, labels, issue point estimates, verification expectations, and sequence.

Research must be written into the source issue or task before creating implementation issues or execution sub-issues. Parent issues must list linked work and summaries, and they may only be marked done after all linked implementation issues and sub-issues are done.

## Core Principle

No important agent context should live only in chat.

When working in a target repository, if an agent discovers something important, it must be written into:

- the task file
- a handoff file
- docs
- an ADR
- or a new append-only work log entry
