# Agentic Development Setup Prompt

Use this prompt to install this protocol into another repository without committing protocol files to that repository.

## Default Install Mode

Default target repository setup is local-only.

The protocol should live in:

```text
.agent-protocol/
```

The target repository should ignore it through:

```text
.git/info/exclude
```

Do not use tracked `.gitignore` for this by default. `.git/info/exclude` is local to one clone and will not be committed.

## How To Use

1. Open the target repository in your coding agent.
2. Give the agent this repository URL and paste the setup prompt below.
3. Ask the agent to inspect the target repository first.
4. Verify that `git status --short` does not show `.agent-protocol/` or any local bootstrap file.

## Copy-Paste Setup Prompt

```text
Set up the Agentic SDLC protocol in this target repository using local-only mode.

Protocol source:
[PASTE_PROTOCOL_REPOSITORY_URL_HERE]

Important:
- Inspect the current repo first.
- Do not implement any product feature.
- Do not overwrite existing files blindly.
- Do not modify tracked .gitignore unless I explicitly request it.
- Do not commit or push protocol files.
- Use .git/info/exclude for local ignore rules.
- Install the full protocol under .agent-protocol/.
- Treat .agent-protocol/ as the protocol root.
- GitHub Issues, issue labels, issue body, comments, linked sub-issues, PRs, and PR comments are the shared source of truth.

First inspect:
- git status --short --branch
- git ls-files AGENTS.md CLAUDE.md SKILLS.md .cursor/rules/project.mdc .github/ISSUE_TEMPLATE
- README files
- package/dependency files
- framework config
- test config
- source folders
- docs/
- .github/ if present
- existing agent docs such as AGENTS.md, CLAUDE.md, SKILLS.md, .cursor/rules/

Local-only install steps:
1. Copy or sync the required protocol source files into .agent-protocol/, preserving their relative paths.
2. Include at least:
   - .agent-protocol/AGENTS.md
   - .agent-protocol/SKILLS.md
   - .agent-protocol/CLAUDE.md
   - .agent-protocol/README.md
   - .agent-protocol/docs/
   - .agent-protocol/multiagent/
   - .agent-protocol/AGENTIC_DEVELOPMENT_SETUP_PROMPT.md
3. Add this local ignore rule to .git/info/exclude:
   /.agent-protocol/
4. If AGENTS.md is not tracked and does not contain user content, create a root AGENTS.md bootstrap with:

   # Local Agent Bootstrap

   Before doing any work in this repository, read:

   .agent-protocol/AGENTS.md

   This file and .agent-protocol/ are local-only agent protocol files. Do not commit or push them.

5. If a local root AGENTS.md bootstrap is created, add this to .git/info/exclude:
   /AGENTS.md
6. If AGENTS.md is already tracked, do not overwrite it. Report that future agent prompts must explicitly say: "Before doing any work, read .agent-protocol/AGENTS.md."
7. Create optional local-only tool adapter bootstraps, such as CLAUDE.md or .cursor/rules/agent-protocol.mdc, only when they are untracked and useful for the user's tool. Add each created adapter path to .git/info/exclude.
8. Do not create tracked .github/ISSUE_TEMPLATE files unless I explicitly request tracked GitHub issue templates.
9. Create or verify GitHub labels when GitHub access is available.
10. Verify with git status --short that no protocol files appear as tracked or untracked changes.

After setup, report:
- where the protocol was installed
- whether root AGENTS.md bootstrap was created
- whether any existing tracked agent files prevented local bootstrap creation
- which .git/info/exclude entries were added
- which GitHub labels were created or already existed
- confirmation that no protocol files are visible in git status --short
```

## GitHub Labels

Create or verify these labels in every project using this protocol.

```text
agent:needs-triage        Issue needs readiness triage before implementation.
agent:needs-clarification Issue needs human clarification before implementation.
agent:needs-breakdown     Issue is too large, vague, or over 8 issue points.
agent:split               Parent issue has been split into linked work.
agent:ready               Issue is clear, scoped, verified, and ready.
agent:in-progress         Agent has claimed and is actively working.
agent:blocked             Blocked by dependency, access, decision, or external issue.
agent:review              Implementation is complete and ready for review.
agent:done                Work is merged, accepted, or explicitly complete.

priority:P0               Urgent priority; handle before all other work.
priority:P1               High priority; handle after P0.
priority:P2               Medium priority; handle after P0/P1.
priority:P3               Low priority; handle after P0/P1/P2.

type:feature              New user-facing or product capability.
type:bug                  Bug fix or regression work.
type:research             Research, investigation, or discovery work.
type:refactor             Internal improvement that preserves behavior.
type:docs                 Documentation-only work.
type:test                 Test coverage, tooling, or verification work.
type:chore                Maintenance or housekeeping work.

issue-points:1            Estimated effort: 1 hour.
issue-points:2            Estimated effort: 2 hours.
issue-points:3            Estimated effort: 3 hours.
issue-points:4            Estimated effort: 4 hours.
issue-points:5            Estimated effort: 5 hours.
issue-points:6            Estimated effort: 6 hours.
issue-points:7            Estimated effort: 7 hours.
issue-points:8            Estimated effort: 8 hours.
issue-points:over-8       Over 8 hours; split into smaller implementation issues.
```

## Local Bootstrap Template

Use `multiagent/templates/local-bootstrap-agents-template.md` as the root `AGENTS.md` bootstrap when the target repository does not already track `AGENTS.md`.

## Final Setup Checklist

- [ ] `.agent-protocol/AGENTS.md` exists.
- [ ] `.agent-protocol/docs/` exists.
- [ ] `.agent-protocol/multiagent/` exists.
- [ ] `.git/info/exclude` ignores `/.agent-protocol/`.
- [ ] Root `AGENTS.md` bootstrap exists only if it is untracked and ignored.
- [ ] Existing tracked agent files were not overwritten.
- [ ] No tracked `.gitignore` change was made unless explicitly requested.
- [ ] No tracked `.github/ISSUE_TEMPLATE` files were added unless explicitly requested.
- [ ] GitHub labels exist when GitHub access is available.
- [ ] `git status --short` does not show protocol files.
- [ ] No product feature implementation was included.
