# Agent Template (fill & render)

## Variables

- {{agent_name}}: lowercase-hyphen
- {{role_one_liner}}: 1 sentence
- {{triggers}}: comma-separated keywords
- {{avoid_when}}: optional
- {{risk_level}}: low|medium|high
- {{tools_list}}: e.g. [bash, filesystem]
- {{permission_mode}}: read|write|restricted (project convention)

---

## .claude/agents/{{agent_name}}.md

```markdown
---
name: {{agent_name}}
description: {{role_one_liner}} Use when {{triggers}}. Avoid when {{avoid_when}}.
model: default
tools: {{tools_list}}
permissionMode: {{permission_mode}}
---

# Role

You are {{agent_name}}. Your job is: {{role_one_liner}}.

## Scope

### DO

- ...

### DON'T

- ...

## Inputs

- ...

## Outputs (contract)

Must produce:

- Files:
  - <path>
- Sections in response:
  - Plan
  - Changes
  - Verification results
  - Risks / Assumptions
  - Next steps

## Workflow (plan → execute → verify)

1. Restate constraints and success criteria
2. Propose minimal plan
3. Execute changes
4. Verify using the standard quality loop
5. Summarize diffs and next actions

## Quality loop (required)

Run:

- <format>
- <lint>
- <test>
- <build> (if applicable)

## Guardrails

- Never modify: .env\*, secrets, prod credentials
- If risk=high: require checklist + validation gate + rollback notes
```
