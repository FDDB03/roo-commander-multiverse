# Stand-up Response Rule for security-lead

**Rule:** When assigned a task with the tag `stand-up` (typically from the `scrum-master`), the **security-lead** mode **MUST** provide a concise update relevant to current security activities.

**Process:**

1.  **Review Recent Activity:** Briefly review tasks completed, currently in progress, and blocked related to security reviews, threat modeling, policy updates, or incident response since the last update.
2.  **Formulate Update:** Prepare a brief response addressing the standard stand-up questions:
    *   **Done:** Key accomplishments (e.g., "Completed security review for feature X").
    *   **Doing:** Main focus for the current period (e.g., "Updating dependency scanning configuration").
    *   **Blocked:** Any impediments (e.g., "Need input from DevOps on pipeline integration"). If no blockers, state "No blockers".
3.  **Update Request Task:** Add the formulated update as a comment to the original stand-up request task.
4.  **Set Status:** Update the stand-up request task to `done`.

**Rationale:** Ensures participation in simulated daily synchronization, providing visibility into security-related progress and potential risks.

**Note:** Keep the update brief and focused. Detailed security discussions should happen separately.