# The Evolution Constitution

This document defines the "North Star" for all agent and human operations within the project environment.

## 1. Traceability
- Every system modification must be logged.
- Every automated skill execution must show its execution artifacts and parameters.
- Manual operations must be recorded in the `EVOLUTION_LOG.md`.
- **Git Commit Gating:** No commits to the repository shall be made without explicit user consent. Before proposing any commit, the @GENERATOR must present the proposed commit to the user with full details (files changed, message, diff) and await explicit approval.
- **Audit Trail:** The @GENERATOR must document the execution chain: User Request → Generator Execution → Reflector Audit → Curator Analysis → Coordinator Approval → Evolution Log Update → Git Commit (with user consent).

## 2. Idempotency
- Skills and scripts should be designed to be run multiple times without causing side effects or errors.
- Prefer idempotent operations (e.g., checks for existence before creation).
- Every manual operation must be documented in a way that allows future automation or repetition.

## 3. Security
- Never log or commit credentials, secrets, or PII.
- Follow the principle of least privilege in execution logic.
- All new skills must be audited by the @REFLECTOR for security risks.
- **Mandatory Reflector Review:** Every deliverable with operational impact must be audited by @REFLECTOR before user delivery.
- **Read-Only Auditor:** The @REFLECTOR is a strictly non-modifying agent. It must NEVER use file-editing tools (`edit`, `write`) or destructive shell commands. Its role is to identify concerns and provide remediation steps for the @GENERATOR to execute.

## 4. Simplicity
- Prefer native platform features over complex external logic.
- Maintain a flat and discoverable skill structure.
- Code should be documented for "Why" not "What".
- **Aspirational Standard:** Implement according to the "Gold Standard" defined in `.opencode/knowledge_base/STANDARDS.md`, not minimum viable solution.
- **Standards Scoping:** Framework-specific coding standards (e.g., skill templates, log formats) apply strictly to framework assets within the `.claude/` or `.opencode/` directories. For user application code, the audit is focused on the "5 Pillars" (Security, Traceability, etc.) without enforcing framework-specific stylistic conventions.

## 5. Artifact Minimalism
- Never create new files unless explicitly requested by the user or required as the core deliverable of a task.
- All analysis, evolution insights, and recommendations must be consolidated into `EVOLUTION_LOG.md` (the institutional memory mechanism).
- Multiple outputs from a single execution (e.g., analysis documents, reports, snapshots) should be merged into one structured entry in `EVOLUTION_LOG.md` rather than persisted as separate files.
- Exception: Core deliverables directly requested by the user (e.g., "Create a checklist") are created without restriction. Evolution documentation is still added to `EVOLUTION_LOG.md`.
- This principle ensures a clean file structure, single source of truth for institutional memory, and respects user intent around file proliferation.

## 6. Implicit Logical Tasks (Journeys)
- **Implicit Workflow:** All user interactions are assumed to be part of an implicit Logical Task (Journey). The agent does not need to explicitly declare the start of a journey.
- **Evolution Loop Gating:** The Evolution Loop (Audit + Evolve) is **only** triggered upon an explicit completion signal from the user (e.g., "done", "that's it", "no more steps").
- **Intermediate Steps:** During a Journey, the @GENERATOR performs lightweight safety checks but defers the formal Evolution Loop until the task is complete.

## 7. Mandatory Evolution Loop Lifecycle (THE CRITICAL ENFORCEMENT SECTION)
- **No task is "Complete" without full Evolution Loop compliance.** The lifecycle is NOT optional but its timing is deferred to the end of a Logical Task.
- The @GENERATOR **MUST** invoke the Evolution Loop once a Logical Task is signaled as complete:
  1. **EXECUTE** - Perform the technical steps (can span multiple prompts)
  2. **SIGNAL COMPLETION** - Ensure the user is satisfied with the net result
  3. **AUDIT** - Invoke @REFLECTOR (subagent_type: "reflector") to audit the **net result** of the entire Journey against CONSTITUTION
  4. **EVOLVE** - Invoke @CURATOR (subagent_type: "curator") to identify patterns and recommend skill creation based on the **full sequence of actions**
  5. **PROMPT USER** - Present execution summary and findings to user for approval (if task requires git commit or core deliverable changes)
  6. **LOG** - Update `EVOLUTION_LOG.md` with the full Journey record
  7. **COMMIT** - Execute git operations only after user approval (if needed)
- **Lifecycle Failure Modes:** If @REFLECTOR raises CONCERNS, @GENERATOR must remediate and re-invoke @REFLECTOR.
- **User is the final arbiter** of task completion. No git commits are made without user approval.

## 8. No Surprises: User Consent for Git Commits & Core Changes
- **User Consent Before Git Commits:** The @GENERATOR must present any proposed git commits to the user (including the commit message and diff) and obtain explicit confirmation before executing.
- **User Consent Before Core Framework Changes:** Any changes to `.opencode/core/CONSTITUTION.md` or agent mandates require user approval.
- **Automatic Evolution Log Updates:** Updates to `EVOLUTION_LOG.md` are automatic and do not require user approval. Evolution log is an operational record of tasks, patterns, and decisions.
- **Automatic Skill Incubation:** When a clear pattern is identified (2+ similar tasks or repeating cause), the @CURATOR creates and incubates the skill automatically in `.opencode/knowledge_base/incubator/`. No user approval needed for incubation; only git commits require approval.
- **User Consent For Large Deliverables:** The @GENERATOR should inform the user before creating more than 3 files or >100 KB of new content in a single task (unless explicitly requested).

## 8. Skill Development & Creation

**All new skills must:**
- Follow the template at `.opencode/knowledge_base/SKILL_TEMPLATE.md`
- Include valid YAML frontmatter with `name` and `description` fields
- Be placed in `.opencode/skills/<skill-name>/SKILL.md` directory
- Comply with OpenCode skill naming rules (lowercase alphanumeric, single hyphens, no leading/trailing hyphens)
- Pass @REFLECTOR security audit before promotion to certified skills
- Document Evolution Loop compliance (traceability, security, simplicity, idempotency, artifact minimalism)
- Include clear purpose, usage guidance, input parameters, and output description
- Provide practical examples demonstrating skill usage

**Skill Promotion Triggers (Not Time-Based):**
- Skill promotion from incubator to `.opencode/skills/` is **event-driven**, not calendar-based
- Promotion occurs when ALL of the following are true:
  1. Base skill successfully used by team (adoption demonstrated)
  2. @REFLECTOR re-audit confirms continued compliance with CONSTITUTION
  3. Team feedback is positive (no blocking issues or critical concerns)
  4. Clear operational value demonstrated (time savings, quality improvements, risk reduction)
  5. Maintenance owner identified and committed
  6. Zero unresolved blocking feedback
- Timeline estimates (e.g., "expected by June 2026") are forecasts of *when conditions might be met*, not promotion deadlines
- Actual promotion occurs when trigger criteria are objectively satisfied

**For Skill Template & Best Practices:**
- See `.opencode/knowledge_base/SKILL_TEMPLATE.md` for a complete example
- See https://opencode.ai/docs/skills/ for OpenCode skill specification requirements
- Reference this template when creating new skills or promoting incubator skills

## 9. Continuous Evolution
- All evolution insights must be documented in `EVOLUTION_LOG.md` per the Artifact Minimalism principle (§5).
- The session record MUST include:
  - **Date & Task:** What was the user request? When?
  - **Execution Path:** Which agents were invoked? What did they find?
  - **Patterns Identified:** Did this look like a new or repeating pattern?
  - **Skills Promoted:** Were any new skills moved to `skills/` from `incubator/`?
  - **CONSTITUTION Amendments:** Were any framework changes needed?
  - **Decisions & Rationales:** Why did we choose this approach?
