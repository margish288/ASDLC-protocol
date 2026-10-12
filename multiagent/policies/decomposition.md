# Research And Decomposition Policy

Apply this policy to the selected tracker. In GitHub mode, records are Issues and descriptions are issue bodies. In Local mode, records are task files and descriptions are their Markdown bodies. Keep the same requirements in both modes.

When the source is documentation rather than a task, use `multiagent/policies/document-intake.md` first for source discovery, scope classification, provenance, and duplicate detection. Do not require the user to create the source task manually.

## Research First

Before splitting, creating execution sub-issues, or implementing:

- Read the requirement, comments/history, related records, repository docs, affected code, tests, and configuration.
- Identify dependencies, risks, unknowns, and verification expectations.
- Estimate implementation, verification, and documentation together: one issue point equals one hour.
- Write a concise research summary and estimate in the source/parent description.
- Ask for clarification when product behavior, acceptance criteria, scope, security, payment, or data behavior is unresolved.

Capturing a new request as a backlog record is allowed before research. It must not be presented as ready implementation work. Do not create a detailed decomposition from guesses.

## Separate Implementation Items

An implementation item should fit one focused PR and have an estimate of eight issue points or less.

An oversized source item must be divided into separate implementation items, not execution sub-issues. Link these independent records from the original tracking parent. Research each independently before coding or creating its own execution children.

Also split when independent acceptance criteria, unrelated changes, or multiple PRs require separately verifiable deliverables. Do not create artificial tiny tasks. If safe atomic work cannot fit the limit, clarify or reduce scope before implementation; do not declare it ready by exception.

After decomposition, mark the source parent split, remove ready status, and maintain its description with the research, links, sequence, dependencies, progress, blockers, and remaining work.

## Execution Children

Within a researched implementation item of at most eight points, create execution children when separable steps merit independent tracking.

- GitHub: use native parent/sub-issue relationships when available, and list the children in the parent's description. If native linking is unavailable, record that limitation and explicit reciprocal links.
- Local: create child task records with `kind: execution` and a `parent` reference, and maintain the parent's `execution_children` list. Validate both directions and reject cycles.
- Separate implementation items use `kind: implementation` and `tracking_parent`; they are listed under `implementation_items`, not execution children.
- Work children individually, respecting dependencies. Avoid unbounded recursive splitting of small steps.

Each record includes identity, parent/tracking-parent link as applicable, goal, acceptance criteria, dependencies, research, findings/fixes, verification, priority/type, estimate, and sequence.

## Parent Progress

Descriptions must show linked work and current progress, not just scattered comments. Preserve user-authored content and concurrent edits when updating descriptions.

Summarize findings, fixes, and evidence after each child's review/completion. Parents can enter review when required children are review-ready or done. Mark a parent done only after required linked work is done, following the task-status policy. Cancellation or scope removal needs explicit explanation and revised acceptance criteria; it does not count as completed work.

Use `multiagent/templates/requirements-breakdown-template.md` for the research and breakdown format.
