---
name: example-skill
description: Brief description of what this skill does (1-1024 characters)
license: MIT
compatibility: opencode
metadata:
  audience: developers
  category: example
---

# Example Skill Template

This is a template for creating new skills in the Evolution Loop framework. Use this as a starting point for any new skill you develop.

## Purpose

Clear, concise explanation of what this skill does and the problem it solves.

## When to Use

Describe the scenarios where this skill should be loaded and used. Help agents understand when to invoke this skill.

## How It Works

Step-by-step explanation of how the skill operates. Include any important context about dependencies, prerequisites, or assumptions.

### Prerequisites

- List any required setup
- Document dependencies
- Note any configuration needed

### Input Parameters

If your skill accepts parameters, document them here:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| param1 | string | yes | Description of param1 |
| param2 | boolean | no | Description of param2 |

### Process

Walk through the main steps the skill performs.

## Output

Describe what the skill delivers:
- What artifact(s) are produced?
- What format are results in?
- How can agents use the output?

## Example Usage

Provide a concrete example of using this skill.

```
skill({ name: "example-skill" })
```

### Expected Result

Show what the output looks like.

## Framework Compliance

This skill follows Evolution Loop principles:

- ✅ **Traceability** — All operations logged in EVOLUTION_LOG
- ✅ **Security** — No credentials/secrets embedded
- ✅ **Simplicity** — Single, well-defined purpose
- ✅ **Idempotency** — Safe to run multiple times
- ✅ **Artifact Minimalism** — Produces only necessary outputs

## Troubleshooting

### Issue: [Common Problem]
**Solution:** [How to resolve]

## Related Skills

Link to other related skills or references in the framework.

## Notes

Any additional context, known limitations, or future improvements.

---

## Creating Your Own Skill

**To create a new skill:**

1. Create directory: `.claude/skills/<skill-name>/`
2. Create `SKILL.md` file with:
   - Valid frontmatter (required fields: `name`, `description`)
   - Name must match directory name (lowercase, hyphens only, no leading/trailing hyphens)
3. Document purpose, usage, inputs, outputs
4. Add examples for clarity
5. Verify compliance with Evolution Loop principles

**Validation checklist:**
- [ ] Name is lowercase alphanumeric with single hyphens only
- [ ] Name matches directory name
- [ ] `description` is 1-1024 characters
- [ ] Frontmatter is valid YAML
- [ ] File is named `SKILL.md` (all caps)
- [ ] Purpose and usage are clear
- [ ] Examples are provided
- [ ] Evolution Loop compliance verified

**For more details:**
- See `.claude/core/CONSTITUTION.md` for framework principles
- See `.claude/knowledge_base/STANDARDS.md` for project conventions
- See `.claude/knowledge_base/EVOLUTION_LOG.md` for pattern history
- Refer to your project's internal documentation for specific API or environment requirements.
