# Validation loops (quality-critical)

## Default loop

plan → validate → apply → verify

## High-risk operations (must be low freedom)

- migrations
- deployments
- destructive edits (deletes, secrets, infra/prod)

## High-risk checklist pattern

- [ ] plan file created
- [ ] validator run and passed
- [ ] changes applied
- [ ] verification (tests/build/smoke) passed
- [ ] rollback plan documented

## Validators should be deterministic

- print "OK" or "ERROR: <reason>"
- include actionable error messages
