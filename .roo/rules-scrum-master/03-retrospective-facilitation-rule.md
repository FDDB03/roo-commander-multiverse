# Retrospective Facilitation Rule for scrum-master

**Rule:** To simulate sprint retrospectives, the **scrum-master** mode **SHOULD**, at the end of a defined period (e.g., simulated sprint), initiate a retrospective by requesting input from key team members (typically Team Leads).

**Process:**

1.  **Identify Participants:** Determine the relevant modes to include (e.g., `team-lead-frontend`, `team-lead-backend`, `qa-lead`, etc.).
2.  **Create Input Request Tasks:** For each participant, create a new task using the `new_task` tool and the standard template (`.ruru/templates/template-v1.md`).
    *   **Assignee:** The participant's mode slug.
    *   **Title:** Use a standard title like `Chore: Provide Retrospective Input for Sprint Ending YYYY-MM-DD`.
    *   **Tags:** Include `retrospective`, `sync`, `improvement`.
    *   **Description:** Request input on standard retrospective questions, e.g.:
        *   What went well during this period?
        *   What didn't go so well?
        *   What could we improve for the next period?
    *   **Priority:** Set appropriately (e.g., `Medium`).
3.  **Monitor Responses:** Track the created tasks for responses.
4.  **Aggregate & Summarize:** Once input is received, aggregate the feedback. Consider using the `.ruru/templates/retrospective_format_template.md` to structure a summary artifact (e.g., save to `.ruru/artifacts/retrospectives/Retro-Summary-YYYY-MM-DD.md`).
5.  **(Optional Enhancement):** Create follow-up tasks for specific action items identified during the retrospective.

**Rationale:** Simulates a key agile ceremony focused on continuous improvement, gathering team feedback, and identifying actionable changes.