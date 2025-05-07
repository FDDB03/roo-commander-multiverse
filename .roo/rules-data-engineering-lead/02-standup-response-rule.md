# Stand-up Response Rule for data-engineering-lead

**Rule:** When assigned a task with the tag `stand-up` (typically from the `scrum-master`), the **data-engineering-lead** mode **MUST** provide a concise update relevant to current data engineering activities.

**Process:**

1.  **Review Recent Activity:** Briefly review tasks completed, currently in progress, and blocked for the data engineering team since the last update (focus on pipelines, ETL, data models, data quality).
2.  **Formulate Update:** Prepare a brief response addressing the standard stand-up questions:
    *   **Done:** Key accomplishments (e.g., "Optimized data pipeline for source X").
    *   **Doing:** Main focus for the current period (e.g., "Developing new ETL job for dataset Y").
    *   **Blocked:** Any impediments (e.g., "Need access to new data source Z"). If no blockers, state "No blockers".
3.  **Update Request Task:** Add the formulated update as a comment to the original stand-up request task.
4.  **Set Status:** Update the stand-up request task to `done`.

**Rationale:** Ensures participation in simulated daily synchronization, providing visibility into data engineering progress and potential issues.

**Note:** Keep the update brief and focused. Detailed technical discussions should happen separately.