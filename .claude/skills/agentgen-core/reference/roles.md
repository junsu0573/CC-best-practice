# Agent role patterns (reusable)

## Core agents (universal set)

- planner: decomposes tasks, risks, milestones, acceptance criteria
- implementer: makes minimal code changes with tests
- reviewer: reviews diffs, edge cases, performance, conventions
- tester: adds/updates tests, builds smoke scenarios
- release-operator: deploy/migrate/rollback with strict commands
- docs-writer: updates README/CHANGELOG/ops docs

## Split by responsibility (recommended)

- Keep agents narrow and composable
- Prefer one responsibility per agent (SRP)
- Use delegation via description triggers
