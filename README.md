# GitHub Defaults

This repository is the account-wide source of truth for software work intake, issue templates, and shared GitHub workflow conventions.

## Canonical standard

See [WORK_INTAKE.md](./WORK_INTAKE.md).

## Default issue forms

The forms in `.github/ISSUE_TEMPLATE/` are inherited by repositories owned by this account unless a repository defines its own issue-template configuration.

## Work classification

Each normal software issue should have:

- exactly one `type:*` label;
- exactly one `state:*` planning-state label.

Operational execution status belongs in the Software Development GitHub Project rather than in planning-state labels.

## New-project routing

Ideas for software that does not yet have an implementation repository should be captured in `mnbohannon/software-planning` until a dedicated repository is warranted.
