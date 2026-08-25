---
source_issue:
triage_outcome: agent:needs-breakdown
triaged_by:
created_at: YYYY-MM-DD
updated_at: YYYY-MM-DD
---

# Requirements Breakdown

## Source Issue

- Issue:
- Title:
- Link:

## Requirement Summary

Summarize the requested outcome in plain language.

## Research Summary

Record what was inspected before creating implementation issues or execution sub-issues.

- Issue description/comments:
- Relevant docs:
- Relevant code/tests:
- Dependencies:
- Risks/unknowns:
- Verification expectation:

## Issue Points

```text
1 issue point = 1 hour of expected implementation, verification, and documentation work
```

Issues over 8 issue points should be split into separate implementation issues before coding, not execution sub-issues.

## Readiness Check

- [ ] clear goal
- [ ] clear acceptance criteria
- [ ] enough context to begin
- [ ] test or verification expectation
- [ ] reasonable scope for one PR
- [ ] estimated at 8 issue points or less
- [ ] no unresolved product decision
- [ ] dependencies are known

Issue point estimate:

- Parent estimate:
- Split into separate implementation issues required because estimate is over 8 issue points: yes/no
- Execution sub-issues needed after implementation issue research: yes/no

## Ambiguities / Questions

- Question 1:
- Question 2:

## Proposed Implementation Issues

Use this section when the source issue is over 8 issue points. These are separate implementation issues, not execution sub-issues.

### 1. Implementation Issue Title

Goal:

Acceptance criteria:

- [ ] Criterion 1
- [ ] Criterion 2

Dependencies:

- Depends on:
- Blocks:

Labels:

- `agent:ready`
- `priority:P2`
- `type:feature`
- `issue-points:1`

Issue points:

- 1

Verification:

- Expected command or manual check:

Sequence:

- 1

Parent issue update summary:

- Research summary to add:
- Link/status line to add:
- Remaining work summary:

## Proposed Execution Sub-Issues

Use this section after researching a ready implementation issue estimated at 8 issue points or less.

### 1. Execution Sub-Issue Title

Parent issue link:

Platform parent/sub-issue link:

Goal:

Acceptance criteria:

- [ ] Criterion 1
- [ ] Criterion 2

Dependencies:

- Depends on:
- Blocks:

Research findings:

- Finding 1:

Implementation or fix notes:

- Note 1:

Labels:

- `agent:ready`
- `priority:P2`
- `type:feature`
- `issue-points:1`

Issue points:

- 1

Verification:

- Expected command or manual check:

Sequence:

- 1

## Parent Issue Updates

- [ ] Add `agent:split`
- [ ] Remove `agent:ready`
- [ ] Add research summary to parent issue description
- [ ] Link all implementation issues or execution sub-issues
- [ ] Use platform parent/sub-issue relationships where available
- [ ] Add progress checklist to parent
- [ ] Add finding and fix summaries to parent as linked work completes
- [ ] Leave parent open until all linked implementation issues and execution sub-issues are done
