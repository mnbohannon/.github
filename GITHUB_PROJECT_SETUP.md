# Software Development GitHub Project Setup

This document defines the canonical GitHub Project used to manage execution across repositories.

> The GitHub connector currently used by ChatGPT can read and write repository issues and files, but it does not expose GitHub Projects v2 creation or field-management mutations. Therefore this document is the authoritative setup specification for the Project UI.

## Project

Create a user-level GitHub Project named:

`Software Development`

Use a table layout initially.

## Status field

Configure the built-in Status field with these values, in this order:

1. Inbox
2. Backlog
3. In Progress
4. Review
5. Done
6. Cancelled

This field represents execution status only.

Do not use Status to represent planning maturity. Planning maturity is represented by the `state:*` labels defined in `WORK_INTAKE.md`.

## Priority field

Create a Single Select field named:

`Priority`

Values:

- P0 — Critical
- P1 — High
- P2 — Normal
- P3 — Low

Do not auto-assign Priority during intake unless the user explicitly sets one. New work should normally enter with Priority unset.

## Execution Target field

Create a Single Select field named:

`Execution Target`

Values:

- Unassigned
- Local Agent
- Codex
- Claude Code
- Human

This field identifies the intended execution environment, not the issue type.

## Recommended optional fields

Add only if they become useful:

- Target Date
- Estimate
- Release

Avoid adding fields merely because GitHub supports them.

## Views

### Intake

Layout: Table

Filter:

`status:Inbox`

Purpose: newly created work awaiting triage.

### Agent Queue

Layout: Table

Filter:

`label:"state:agent-ready" status:Backlog`

Purpose: work that has been planned sufficiently for an execution agent but has not yet started.

### Active

Layout: Board

Group by: Status

Filter:

`status:"In Progress","Review"`

Purpose: currently executing or reviewing work.

### Initiatives

Layout: Table

Filter:

`label:"type:initiative"`

Purpose: larger outcomes and their progress.

### Research

Layout: Table

Filter:

`label:"type:research"`

Purpose: open investigations and decisions.

## Auto-add behavior

Configure GitHub Project auto-add workflows for actively developed repositories.

The preferred query is:

`is:issue`

Newly added issues should enter with:

- Status = Inbox
- Priority = unset
- Execution Target = Unassigned

Do not automatically change planning-state labels in the Project. Those labels are controlled by issue planning.

## Issue lifecycle example

A normal feature may progress as follows:

1. Issue created with `type:feature` and `state:exploring`.
2. Project auto-adds the issue with Status = Inbox.
3. Requirement refinement moves the issue to `state:defined`.
4. Triage moves Project Status to Backlog.
5. Repository analysis and implementation planning moves the issue to `state:planned`.
6. Once the implementation plan is sufficiently detailed for the intended execution target, replace `state:planned` with `state:agent-ready`.
7. When execution begins, Project Status becomes In Progress.
8. Pull-request or implementation review moves Project Status to Review.
9. Completion moves Project Status to Done.

Planning state and execution status must remain separate throughout this lifecycle.

## Parent and sub-issues

Use GitHub parent/sub-issue relationships for Initiative decomposition.

- Initiative: larger outcome.
- Feature / Research / Technical Debt: independently meaningful child work.
- Task: narrowly scoped implementation work where additional decomposition is useful.

Avoid using plain Markdown checklists as a substitute for actual sub-issues when the child work should be tracked independently.
