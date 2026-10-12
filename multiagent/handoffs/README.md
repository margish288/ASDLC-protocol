# Handoffs

Keep the primary handoff in the selected tracker: the Local task description or GitHub Issue/PR. Use `multiagent/templates/handoff-template.md`.

A separate file is optional for complex durable context or an explicit request. Store it under the configured target state location, link it from the task, and make it accessible to the receiving agent. An ignored local file is not a cross-machine handoff.

Include current status, owner/claim transfer, branch/worktree, changed files, evidence, remaining work, blockers, risks, and next action. Preserve unfinished user work.

Do not create live handoffs in this protocol source repository.
