# Contributing

Thank you for your interest in improving Claude Code Best Practice!

## How to Contribute

### 1. Improve existing templates

- **Skills**: Edit files in `.claude/skills/skillgen-core/`
- **Agents**: Edit files in `.claude/skills/agentgen-core/`
- Follow the existing structure and naming conventions
- Keep changes focused and minimal

### 2. Add new reference documents

Create new files in `reference/` for:
- Common patterns not yet documented
- Edge cases and workarounds
- Examples from real-world usage

### 3. Propose structural changes

For significant changes:
1. Open an issue first to discuss
2. Explain the problem and proposed solution
3. Wait for feedback before implementing

## Guidelines

### Skill Structure

```
.claude/skills/<skill-name>/
├── SKILL.md              # Required: main entry
├── reference/*.md        # Optional: 1-level deep only
├── scripts/*             # Optional: validators
└── eval/*.json           # Required: >= 3 test cases
```

**SKILL.md Rules:**
- Keep under 300 lines (hard limit: 500)
- Include: quick start, workflow, output contract, guardrails
- Use 1-level deep references only

### Agent Structure

```
.claude/agents/<agent-name>.md
```

**Agent file must include:**
- Frontmatter: name, description, model, tools, permissionMode
- Role: one-sentence job definition
- Scope: explicit DO / DON'T lists
- Outputs: required files and response sections
- Quality loop: verification steps
- Guardrails: sensitive paths, escalation conditions

**Agent principles:**
- Least privilege: minimal tool sets
- Single responsibility: one role per agent
- Clear boundaries: explicit DO / DON'T

### Description Format (Skills & Agents)

```
Does <WHAT>. Use when <WHEN/TRIGGERS>. Avoid when <AVOID>.
```

- Third-person voice
- Max 1024 characters
- Include trigger keywords users actually say

### Naming

- Lowercase letters, numbers, hyphens only
- Max 64 characters
- Prefer gerund form: `processing-pdfs`, `testing-code`
- Avoid vague names: `utils`, `helper`, `tools`

## Pull Request Process

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Make your changes
4. Test locally with Claude Code
5. Submit a pull request with:
   - Clear description of changes
   - Why the change is needed
   - Any breaking changes noted

## Code of Conduct

- Be respectful and constructive
- Focus on improving the project
- Help others learn and contribute

## Questions?

Open an issue for:
- Clarification on guidelines
- Discussion of new ideas
- Reporting problems
