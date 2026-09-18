# Software Work Intake Standard

This document is the canonical standard for software work intake and planning across repositories owned by this account.

## 1. Work Types

Every issue should have one primary work type.

- **Bug** — Existing behavior is incorrect.
- **Feature** — Adds a capability that does not currently exist.
- **Improvement** — Improves an existing capability without fundamentally introducing a new one.
- **Technical Debt** — Refactoring, architecture, maintainability, dependency, migration, or internal engineering work.
- **Research** — Investigation whose primary output is knowledge, a recommendation, a prototype, or a decision.
- **Initiative** — A larger outcome that should be decomposed into multiple independently executable issues.
- **Task** — A concrete unit of implementation work, usually subordinate to a Feature or Initiative.

"Idea" and "long-term" are not work types. They describe maturity or planning horizon.

## 2. Planning States

Issues progress through the following planning states:

1. **Exploring** — The idea or problem has been captured, but important product or technical questions remain.
2. **Defined** — The desired outcome, boundaries, and acceptance criteria are sufficiently clear.
3. **Planned** — The technical approach has been investigated and an implementation strategy exists.
4. **Agent Ready** — The work has an implementation plan sufficiently detailed for the intended execution agent.

Planning state is separate from implementation status.

## 3. Operational Status

Project execution uses:

- Inbox
- Backlog
- In Progress
- Review
- Done
- Cancelled

Operational status belongs in the GitHub Project. It must not be conflated with planning state.

For example, an issue may be `state:agent-ready` while its Project status is still `Backlog`.

## 4. Repository Routing

- If work modifies an existing software project, create the issue in that project's implementation repository.
- If no implementation repository exists yet, create the issue in `mnbohannon/software-planning`.
- Cross-repository outcomes should normally have an Initiative in `software-planning`, with implementation issues in the affected repositories.

## 5. Issue Body Standard

Software issues should contain, where applicable:

### Summary
A concise description of the requested change.

### Problem / Motivation
Why the work is useful or necessary.

### Desired Behavior
The observable end state.

### Scope
What is included.

### Non-goals
Related work explicitly excluded.

### Acceptance Criteria
Observable conditions that establish completion.

### Context
Screenshots, code findings, related issues, constraints, prior decisions, or other relevant evidence.

## 6. Product Requirement vs. Implementation Plan

The issue body is the durable statement of **what should change and why**.

Detailed implementation instructions should normally be added separately as an issue comment after repository analysis.

Implementation plans may change without requiring the underlying product requirement to be rewritten.

## 7. Implementation Plan Requirements

An implementation plan should be appropriate for the intended agent, model, and harness.

A lower-capability or local implementation agent requires:

- explicit task boundaries;
- relevant files and components;
- implementation sequence;
- expected interfaces and behavior;
- tests to create or modify;
- validation commands;
- failure conditions;
- completion criteria;
- explicit non-goals.

A higher-capability implementation or review agent may receive a less prescriptive plan where independent technical reasoning is desirable.

## 8. Initiative Decomposition

Do not turn large outcomes into monolithic implementation issues.

Use an Initiative as the parent and create independent child issues for meaningful features, research, technical debt, and implementation tasks.

An Initiative is complete when its intended outcome has been achieved, not merely when one implementation task closes.

## 9. Classification Invariants

Normal work issues should have:

- exactly one `type:*` label;
- exactly one `state:*` label.

Standard work-type labels:

- `type:bug`
- `type:feature`
- `type:improvement`
- `type:technical-debt`
- `type:research`
- `type:initiative`
- `type:task`

Standard planning-state labels:

- `state:exploring`
- `state:defined`
- `state:planned`
- `state:agent-ready`

Area labels such as `area:ui`, `area:backend`, or `area:infra` are repository-specific and should only be created when useful.

## 10. ChatGPT Intake Behavior

When ChatGPT is used as the intake and planning layer:

1. Determine whether the user is brainstorming or explicitly asking to create/update GitHub work.
2. Select the correct repository.
3. Search for likely duplicate or overlapping issues when appropriate.
4. Inspect relevant repository context when doing so would materially improve the request.
5. Classify the issue with one work type and one planning state.
6. Write the durable product requirement in the issue body.
7. Keep detailed implementation planning separate unless explicitly requested.
8. When implementation planning is requested, inspect the repository and add the plan as an issue comment tailored to the intended execution agent.
