---
name: agentgen-core
description: Generates Claude Code sub-agents (agents/*.md) from a standard template with clear scope, tool constraints, output contracts, and quality loops. Use when creating or standardizing agents, improving delegation triggers, and enforcing guardrails for risky operations.
---

# Agent Generator Core

## When to use

- Creating new agents under `.claude/agents/`
- Refactoring agents to be safer: tighter scope, fewer tools, clear contracts
- Standardizing agent descriptions to improve auto-delegation accuracy
- Adding quality loops (lint/test/build) and risk guardrails

## Inputs (required)

- Agent name (lowercase-hyphen recommended)
- Role (one sentence)
- Triggers/keywords (what requests should route here)
- Scope: DO / DON'T
- Risk level: low | medium | high
- Tools allowed (minimal set)

## Output contract

Creates or updates:

- `.claude/agents/<agent-name>.md` (agent definition)
  Optionally suggests:
- related slash commands (e.g., /verify, /lint, /test)
- hooks/policy check steps (but does not require them)

## Workflow (plan → validate → apply → verify)

1. Plan: fill `TEMPLATE.md` sections (metadata, scope, tools, outputs)
2. Validate: run:
   - `python .claude/skills/agentgen-core/scripts/validate_agent.py .claude/agents/<agent-name>.md`
3. Apply: create/update the agent file
4. Verify: ensure at least 3 evals exist and match expected behaviors

## MUST rules

- Agent description is third-person and includes WHAT + WHEN/TRIGGERS + AVOID (optional)
- Agent must have explicit DO/DON'T scope
- Agent must specify minimal tools (least privilege)
- Agent must define Output contract (files + required sections)
- Agent must include a Quality loop (verify steps)
- High-risk agents must:
  - use low freedom (exact commands / no deviations)
  - include checklist + rollback note + validation gate

## References

- Roles & patterns: `reference/roles.md`
- Description recipe: `reference/description.md`
- Tool minimization: `reference/tools.md`
- Boundaries & guardrails: `reference/boundaries.md`
- Quality loop templates: `reference/quality-loop.md`
