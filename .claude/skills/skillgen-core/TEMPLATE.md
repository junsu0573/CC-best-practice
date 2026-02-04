# Skill Template (fill & render)

## Variables

- {{skill_name}}: lowercase-hyphen
- {{risk_level}}: low|medium|high
- {{purpose_one_liner}}: 1 sentence
- {{triggers}}: comma-separated keywords
- {{avoid_when}}: optional

---

## SKILL.md

```markdown
---
name: {{skill_name}}
description: {{purpose_one_liner}} Use when {{triggers}}. Avoid when {{avoid_when}}.
---

# {{skill_name}}

## Quick start

- <one default command or snippet>

## Workflow

1. Plan
2. Validate
3. Execute
4. Verify

## Output contract

- files created/edited:
- invariants:

## Guardrails

- never touch:
- deterministic checks:

## References

- reference/<file>.md
```
