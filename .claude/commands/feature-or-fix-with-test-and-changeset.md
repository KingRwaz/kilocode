---
name: feature-or-fix-with-test-and-changeset
description: Workflow command scaffold for feature-or-fix-with-test-and-changeset in kilocode.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /feature-or-fix-with-test-and-changeset

Use this workflow when working on **feature-or-fix-with-test-and-changeset** in `kilocode`.

## Goal

Implements a new feature or fixes a bug, updating implementation, adding or updating tests, and documenting the change in a .changeset markdown file.

## Common Files

- `packages/opencode/src/**/*.ts`
- `packages/opencode/test/**/*.test.ts`
- `.changeset/*.md`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or create implementation files (usually in packages/opencode/src/...)
- Add or update corresponding test files (usually in packages/opencode/test/...)
- Add a .changeset/*.md file describing the change

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.