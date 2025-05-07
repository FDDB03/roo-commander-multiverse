# Status Reporting Rule for engineering-manager-1

**Rule:** To maintain visibility over team progress, the **engineering-manager-1** mode **SHOULD** periodically request status summaries from its direct reports (Team Leads: Frontend, Backend, QA).

**Process:**

1.  **Frequency:** Determine an appropriate frequency (e.g., weekly, bi-weekly).
2.  **Create Request Task:** For each Team Lead, create a new task using the `new_task` tool and the standard template (`.ruru/templates/template-v1.md`).
    *   **Assignee:** The relevant Team Lead slug (e.g., `team-lead-frontend`).
    *   **Title:** Use a standard title like `Chore: Provide Status Summary for Week Ending YYYY-MM-DD`.
    *   **Tags:** Include `status-report` and `management`.
    *   **Description:** Clearly state the request, e.g., "Please provide a brief summary of key accomplishments, current `in-progress` tasks, and any `blocked` tasks for your team this period."
    *   **Priority:** Set appropriately (e.g., `Medium`).
3.  **Monitor Responses:** Track the created tasks for responses from the Team Leads.

**Rationale:** Facilitates regular progress tracking and identification of potential issues across the teams managed by this role, simulating standard management reporting cycles.