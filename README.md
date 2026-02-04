# Claude Code Skills Best Practice

A standardized template and guidelines for creating high-quality Claude Code Skills.

## What is this?

This repository provides a **skill generator** (`skillgen-core`) that helps you create consistent, well-structured Claude Code Skills following best practices:

- **Progressive disclosure**: Keep SKILL.md short, link to reference files
- **Clear descriptions**: Discovery-critical format (WHAT + WHEN + AVOID)
- **Validation loops**: plan → validate → apply → verify
- **Risk-aware guardrails**: Checklists and rollback plans for high-risk operations

## Quick Start

### 1. Copy to your project

```bash
cp -r .claude/skills/skillgen-core /your-project/.claude/skills/
```

### 2. Generate a new skill

Tell Claude Code:
```
"Create a new skill for <purpose> using skillgen-core"
```

### 3. Structure created

```
.claude/skills/<skill-name>/
├── SKILL.md              # Main entry point (< 300 lines)
├── reference/            # Supporting docs (1-level deep)
│   ├── naming.md
│   └── validation.md
├── scripts/              # Optional deterministic validators
└── eval/                 # Test cases (smoke, regression, high-risk)
```

## Skill Structure Guidelines

| Component | Purpose | Size Limit |
|-----------|---------|------------|
| `SKILL.md` | Quick start, workflow, guardrails | < 300 lines (max 500) |
| `reference/*.md` | Detailed docs, examples | 1-level deep only |
| `scripts/*` | Validators, automation | Deterministic output |
| `eval/*.json` | Test cases | Minimum 3 cases |

## Description Format

The `description` field in SKILL.md frontmatter is critical for discovery:

```yaml
---
name: my-skill
description: Does <WHAT>. Use when <WHEN/TRIGGERS>. Avoid when <AVOID>.
---
```

**Good**: `Extracts text from PDFs. Use when working with PDF files or document extraction.`

**Bad**: `Helps with documents.`

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on:
- Adding new skills
- Improving existing templates
- Proposing structural changes

## License

[MIT](LICENSE) - Feel free to use, modify, and distribute.
