# Stand-up Response Rule for team-lead-platform

**Rule:** When assigned a task with the tag `stand-up` (typically from the `scrum-master`), the **team-lead-platform** mode **MUST** provide a concise update.

**Process:**

1.  **Review Recent Activity:** Briefly review tasks completed, currently in progress, and blocked for the platform team since the last update.
2.  **Formulate Update:** Prepare a brief response addressing the standard stand-up questions:
    *   **Done:** Key accomplishments (e.g., "Released new Terraform module for S3 buckets").
    *   **Doing:** Main focus for the current period (e.g., "Investigating Kubernetes cluster upgrade path").
    *   **Blocked:** Any impediments (e.g., "Need decision on monitoring tool from Architect"). If no blockers, state "No blockers".
3.  **Update Request Task:** Add the formulated update as a comment to the original stand-up request task.
4.  **Set Status:** Update the stand-up request task to `done`.

**Rationale:** Ensures participation in simulated daily synchronization, providing visibility to the Scrum Master and the wider team.

**Note:** Keep the update brief and focused. Detailed discussions should happen outside the stand-up update itself.