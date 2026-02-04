# Agent description recipe (delegation-critical)

## Required

- third-person (no I/we/you)
- includes WHAT + WHEN/TRIGGERS + key terms
- <= 1024 chars

## Recommended format

- `Performs <WHAT>. Use when <WHEN/TRIGGERS>. Avoid when <AVOID>.`

## Trigger terms (use user language)

- actions: implement, refactor, debug, optimize, migrate, deploy, review, test
- context: PR, CI, regression, rollout, rollback
- artifacts: diff, logs, stacktrace, schema, migrations, infra

## Example

- `Performs safe database migrations with strict commands and validation gates. Use when migrating schemas, applying migrations, or planning rollbacks. Avoid for exploratory design discussions.`
