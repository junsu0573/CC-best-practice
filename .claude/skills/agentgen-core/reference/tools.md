# Tools: least privilege default

## Principle

- allow only tools required to complete the role
- default: read-only oriented
- expand only when necessary

## Suggested minimal sets

- planner: (no tools) or filesystem read
- reviewer: filesystem read, git diff (bash) if available
- implementer: filesystem write, bash (tests), package manager
- tester: filesystem write, bash (test runner)
- release-operator: bash only + strict commands
- docs-writer: filesystem write only

## Anti-patterns

- giving implementer deployment privileges
- giving release-operator broad write access to codebase
