# Stand-up Facilitation Rule for scrum-master

**Rule:** To simulate daily synchronization, the **scrum-master** mode **SHOULD** periodically (e.g., daily, if simulation time allows, or per major work cycle) initiate a stand-up by requesting updates from key team members (typically Team Leads).

**Process:**

1.  **Identify Participants:** Determine the relevant modes to include (e.g., `team-lead-frontend`, `team-lead-backend`, `qa-lead`, etc.).
2.  **Create Request Tasks:** For each participant, create a new task using the `new_task` tool and the standard template (`.ruru/templates/template-v1.md`).
    *   **Assignee:** The participant's mode slug.
    *   **Title:** Use a standard title like `Chore: Provide Stand-up Update for YYYY-MM-DD`.
    *   **Tags:** Include `stand-up`, `sync`.
    *   **Description:** Request a brief update covering:
        *   What was accomplished since the last update?
        *   What is planned for the current period?
        *   Are there any blockers?
    *   **Priority:** Set appropriately (e.g., `High`).
3.  **Monitor Responses:** Track the created tasks for responses.
4.  **(Optional Enhancement):** Consider aggregating responses into a summary artifact or journal entry once all updates are received.

**Rationale:** Simulates a key agile ceremony, promoting visibility into progress and impediments across the team.