# Claude Code Best Practice

Standardized templates and guidelines for creating high-quality Claude Code **Skills** and **Agents**.

## What is this?

This repository provides two generators to help you build consistent, well-structured Claude Code extensions:

| Generator | Purpose | Output |
|-----------|---------|--------|
| `skillgen-core` | Create slash-command skills | `.claude/skills/<name>/` |
| `agentgen-core` | Create sub-agents for delegation | `.claude/agents/<name>.md` |

### Core Principles

- **Progressive disclosure**: Keep main files short, link to references
- **Clear descriptions**: Discovery-critical format (WHAT + WHEN + AVOID)
- **Validation loops**: plan → validate → apply → verify
- **Least privilege**: Minimal tool sets for agents
- **Risk-aware guardrails**: Checklists and rollback plans for high-risk operations

## Quick Start

### 1. Copy to your project

```bash
# Copy skill generator
cp -r .claude/skills/skillgen-core /your-project/.claude/skills/

# Copy agent generator
cp -r .claude/skills/agentgen-core /your-project/.claude/skills/
```

### 2. Generate a new skill

```
"Create a new skill for <purpose> using skillgen-core"
```

### 3. Generate a new agent

```
"Create a new agent for <role> using agentgen-core"
```

## Skill Structure

```
.claude/skills/<skill-name>/
├── SKILL.md              # Main entry point (< 300 lines)
├── reference/            # Supporting docs (1-level deep)
├── scripts/              # Optional deterministic validators
└── eval/                 # Test cases (>= 3)
```

| Component | Purpose | Constraint |
|-----------|---------|------------|
| `SKILL.md` | Quick start, workflow, guardrails | < 300 lines (max 500) |
| `reference/*.md` | Detailed docs, examples | 1-level deep only |
| `scripts/*` | Validators, automation | Deterministic output |
| `eval/*.json` | Test cases | Minimum 3 cases |

## Agent Structure

```
.claude/agents/<agent-name>.md
```

| Section | Purpose |
|---------|---------|
| Frontmatter | name, description, model, tools, permissionMode |
| Role | One-sentence job definition |
| Scope | Explicit DO / DON'T lists |
| Outputs | Required files and response sections |
| Quality loop | format → lint → test → build |
| Guardrails | Sensitive paths, escalation conditions |

### Agent Role Patterns

| Role | Responsibility | Tools |
|------|----------------|-------|
| `planner` | Decompose tasks, risks, milestones | read-only |
| `implementer` | Minimal code changes with tests | write, bash |
| `reviewer` | Review diffs, conventions | read-only |
| `tester` | Add/update tests | write, bash |
| `release-operator` | Deploy/migrate/rollback | bash (strict) |
| `docs-writer` | Update documentation | write only |

## Description Format

The `description` field is critical for discovery and delegation:

```yaml
description: Does <WHAT>. Use when <WHEN/TRIGGERS>. Avoid when <AVOID>.
```

**Good**: `Performs safe database migrations with validation gates. Use when migrating schemas or planning rollbacks.`

**Bad**: `Helps with databases.`

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on:
- Adding new skills or agents
- Improving existing templates
- Proposing structural changes

## License

[MIT](LICENSE) - Feel free to use, modify, and distribute.
