---
name: skillgen-core
description: Generates new Claude Code Skills (SKILL.md + reference + scripts + eval) from a standard template. Use when creating or standardizing skills, improving discovery via descriptions, enforcing progressive disclosure, and adding validation loops for risky operations.
---

# Skill Generator Core

## When to use

- Creating a new skill directory with consistent structure
- Refactoring an existing skill to be shorter + 1-level references
- Adding validators, checklists, and eval cases (smoke/regression/high-risk)

## Inputs (required)

- Skill purpose (1 sentence)
- Triggers/keywords (what user will say)
- Risk level: low | medium | high
- Target output dir: `.claude/skills/<skill-name>/`

## Output contract (what this generator produces)

Creates or updates:

- `.claude/skills/<skill-name>/SKILL.md`
- `.claude/skills/<skill-name>/reference/*.md` (1-level deep only)
- `.claude/skills/<skill-name>/scripts/*` (optional, deterministic)
- `.claude/skills/<skill-name>/eval/*.json` (>= 3)

## Workflow (plan → validate → apply → verify)

1. Plan: fill `TEMPLATE.md` placeholders to define:
   - frontmatter (name/description)
   - quick start
   - workflow + guardrails
   - references list (1-level deep)
2. Validate (generator-level): run:
   - `python .claude/skills/skillgen-core/scripts/validate_skill.py .claude/skills/<skill-name>`
3. Apply: create/update files under `.claude/skills/<skill-name>/`
4. Verify: ensure evals exist and are meaningful:
   - smoke: minimal end-to-end behavior
   - regression: prevents repeated mistakes
   - high-risk: strict validation loop (when risk=high)

## MUST rules

- SKILL.md body stays short (prefer < 300 lines; hard limit 500 lines).
- References are ONE level deep from SKILL.md only.
- `description` is third-person and contains:
  - WHAT it does + WHEN to use + key terms + AVOID (optional)
- Provide ONE default approach; only add one “escape hatch”.
- If risk=high:
  - include checklist + validator step + rollback notes.
- Use forward slashes in paths.

## Pointers

- Naming rules: `reference/naming.md`
- Description recipe: `reference/description.md`
- Structure (progressive disclosure): `reference/structure.md`
- Validation loop patterns: `reference/validation.md`
