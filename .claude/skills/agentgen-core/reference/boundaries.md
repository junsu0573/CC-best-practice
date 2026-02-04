# Boundaries & guardrails

## Must include in every agent

- explicit DO / DON'T
- sensitive paths list
- escalation condition

## Sensitive paths (default)

- .env\*, **/secrets/**, **/credentials/**, infra/prod, prisma/migrations (project-specific)

## Escalation conditions

- ambiguous requirements that change user-facing behavior
- destructive operations (delete/drop)
- production changes without rollback plan
