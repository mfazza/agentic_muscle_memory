# Skill Lifecycle Management

## 0. Discovery (The Proactive Trigger)
- **Trigger:** Successful completion of a task by the Generator.
- **Action:** Generator invokes the Curator and Reflector to review the execution output.
- **Goal:** Identify repeatable patterns or improvements to existing skills.

## 1. Incubation
- **Trigger:** A new pattern is identified in the `EVOLUTION_LOG.md`.
- **Action:** Generator creates a folder in `.opencode/knowledge_base/incubator/`.
- **Visibility:** Not discoverable by the main agent.

## 2. Refinement
- **Trigger:** Skill is drafted.
- **Action:** Reflector audits the code and documentation against `CONSTITUTION.md` and `STANDARDS.md`.

## 3. Certification & Promotion
- **Trigger:** Reflector approval.
- **Action:** Curator moves the folder to `.opencode/skills/` (flat structure).
- **Result:** Skill becomes discoverable and "Certified".

## 4. Maintenance
- **Trigger:** Bug report or new requirement.
- **Action:** Curator updates the skill in place or moves it back to incubator if major refactoring is needed.
