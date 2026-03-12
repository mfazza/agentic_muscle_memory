# Technical Standards & Best Practices

## Developer Workflow & CLI Scripting
- **Idempotency:** Scripts must be safe to run multiple times. Use "check-then-act" patterns (e.g., `mkdir -p`, `git branch --list`).
- **Templating:** Use `{{ v_variable_name }}` for parameterization to ensure scripts are reusable across different environments.
- **Environment Awareness:** Always verify prerequisites (e.g., check if a CLI tool is installed) before execution.
- **Error Handling:** Use explicit exit codes and pipe errors to `stderr`.

## Skill Documentation
- Every skill must have a `SKILL.md`.
- Documentation should include:
  - Purpose
  - Prerequisites
  - Input Variables
  - Output description

## Evolution Loop Implementation
- New patterns are captured in `@EVOLUTION_LOG.md`.
- **Skill Candidate Criteria:**
  - **Repetition:** The task has been performed 2x manually OR appears in documented checklists/runbooks.
  - **Parameterization:** The process can be generalized with `{{ v_variable_name }}` parameters.
  - **High Impact:** The task improves visibility into infrastructure costs, security, dependencies, or reduces time by >30%.
  - **Automation Readiness:** Assessed on 1-5 scale (5=ready, 1=needs more data).
  
- **Skill Promotion Funnel:**
  1. **Incubator:** Pattern identified + specification drafted
  2. **Candidate:** Design approved and specification drafted
  3. **Implementation:** Active development + unit testing
  4. **Review:** @REFLECTOR audit + integration testing
  5. **Certified:** Promoted to `.opencode/skills/` with SKILL.md
  
- **Output Artifact Standards:**
  - Skills should produce structured, machine-readable outputs (JSON, CSV, Markdown)
  - All outputs should be versioned/timestamped for auditability
  - Skills should support both **dry-run** and **execute** modes for safety-critical operations
  - Skills should generate human-readable summary reports (Markdown preferred)

## External System Operations
- **Auditability:** When interacting with external APIs (GitHub, Jira, etc.), always include the specific query, filter, or unique identifier (e.g., query strings, resource IDs, or PR numbers) used in the output summary.
- **Data Mapping:** Map technical status IDs or codes to human-readable labels to ensure reports are accessible to non-technical stakeholders.
