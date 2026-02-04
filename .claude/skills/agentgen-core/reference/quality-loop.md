# Quality loop templates

## Standard (web/backend)

- format → lint → test → build

## Minimal (scripts/docs-only)

- lint (if applicable) → targeted tests (if any)

## High-risk (deploy/migrate)

- validate inputs → dry-run (if available) → execute → smoke check → rollback readiness

## Output format (agent response must include)

- Verification results: commands + pass/fail
- If fail: top 3 root causes + minimal fix plan
