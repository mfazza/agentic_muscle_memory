# Agentic Muscle Memory

Agentic Muscle Memory is a self-evolving framework that enables agents to transform repeating patterns of work into permanent, high-quality skills. By mimicking the human process of building muscle memory through repetition, the framework ensures that once a complex task is solved twice, it becomes a reusable, audited, and standardized capability.  

This framework builds on the ACE Framework documented by Qizheng Zhang in [Agentic Context Engineering: Evolving Contexts for Self-Improving Language Models](https://arxiv.org/abs/2510.04618), and it extends it by adding processes, standards, and strategy to enable skill curation through evolving contexts.

## The Architecture of Evolution

The framework operates through a rigorous **Evolution Loop** (Execute → Audit → Evolve) where four key components interact to ensure every action contributes to the system's growth:

### 1. The Agents (The Actors)
*   **@GENERATOR (The Doer):** The primary agent that performs the work. It is responsible for technical execution and driving the entire lifecycle. It cannot declare a task "complete" until it has been audited and analyzed for evolution.
*   **@REFLECTOR (The Guardian):** A specialized sub-agent that audits the Generator's work against the project's "Pillars of Integrity" (Traceability, Security, Simplicity, and Idempotency). It acts as a mandatory gatekeeper.
*   **@CURATOR (The Librarian):** A sub-agent that manages the "institutional memory." It looks at the audited task, compares it to past executions in the Evolution Log, and identifies patterns. It is the agent that "notices" when muscle memory should be formed.

### 2. The Constitution (The North Star)
The Constitution is the immutable set of laws governing all agent behavior. It defines the "North Star" principles—like **Artifact Minimalism** (keeping the codebase clean, avoiding file creation) and **Mandatory Audit** (enforcing safety). It ensures that as agents evolve new skills, they do so within strict safety and quality boundaries.

### 3. The Evolution Log (The Institutional Memory)
This is the central nervous system of the project. It records every task, decision, and pattern identified by the agents.
*   **Relationship:** The **Generator** logs its actions here; the **Reflector** logs its audit results; and the **Curator** uses this log as its primary data source to detect the "repetition" required to trigger skill creation. It is where the "memory" of the system actually resides.

### 4. The Standards (The Gold Standard)
While the Constitution provides the "Why," the Standards provide the "How." They define the technical benchmarks for what a "Certified Skill" looks like (for example, templating standards, documentation requirements).
*   **Relationship:** When the **Curator** identifies a pattern and recommends a new skill, it uses the **Standards** to draft the specification. The **Reflector** then uses these same standards to audit the newly formed skill before it is promoted from "Incubation" to "Certified."

---

## Deployment & Platform Support

The framework is designed to be platform-agnostic and can be integrated into any repository:
- **OpenCode:** Uses the `.opencode/` directory for its native agent definitions and logs.
- **Claude Code:** Uses the `.claude/` directory and root `CLAUDE.md` to guide Claude CLI agents through the same Evolution Loop.

To adopt this in a new project, simply copy either the `.opencode/` or `.claude/` directory into your repository root.

---

## The "Muscle Memory" Flow
1.  **Pattern Recognized:** A task is requested. The **Generator** executes it.
2.  **Integrity Hardened:** The **Reflector** ensures the execution was safe and simple.
3.  **Pathway Ingrained:** The **Curator** sees this task has happened before in the **Evolution Log**.
4.  **Skill Formed:** The **Curator** incubates a new skill based on the **Standards**, which the agents can now use instinctively for all future requests.
