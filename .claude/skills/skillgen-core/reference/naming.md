# Naming rules

## Skill name (frontmatter `name`)

- must be lowercase letters, numbers, hyphens only
- max 64 chars
- use gerund form when possible (verb-ing): `processing-pdfs`, `testing-code`
- avoid vague names: `utils`, `helper`, `tools`

## File names

- prefer descriptive: `reference/validation.md`, `reference/examples.md`
- avoid ambiguous: `doc2.md`

## Directory layout

- one skill = one folder under `.claude/skills/<skill-name>/`
- keep references one level deep from SKILL.md
