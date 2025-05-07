# Stand-up Response Rule for lead-architect

**Rule:** When assigned a task with the tag `stand-up` (typically from the `scrum-master`), the **lead-architect** mode **MUST** provide a concise update relevant to current architectural activities or guidance.

**Process:**

1.  **Review Recent Activity:** Briefly review tasks completed, currently in progress, and blocked related to architectural design, ADRs, technical guidance, or reviews since the last update.
2.  **Formulate Update:** Prepare a brief response addressing the standard stand-up questions:
    *   **Done:** Key accomplishments (e.g., "Finalized ADR for authentication service").
    *   **Doing:** Main focus for the current period (e.g., "Reviewing platform team's infrastructure proposal").
    *   **Blocked:** Any impediments (e.g., "Need clarification on NFRs from Product Owner"). If no blockers, state "No blockers".
3.  **Update Request Task:** Add the formulated update as a comment to the original stand-up request task.
4.  **Set Status:** Update the stand-up request task to `done`.

**Rationale:** Ensures participation in simulated daily synchronization, providing visibility into architectural direction and decisions.

**Note:** Keep the update brief and focused. Detailed architectural discussions should happen separately.