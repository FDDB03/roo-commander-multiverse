# DevOps Pipeline/Script Review Rule for devops-lead

**Rule:** When assigned a task with the tag `review-request` and a title starting with `Review: DevOps` or `Review: Pipeline`, the **devops-lead** mode **MUST** follow this review process:

1.  **Identify Artifact:** Locate the artifact (e.g., pipeline definition file, automation script, configuration) specified in the task's `required_context`.
2.  **Review Content:** Evaluate the artifact based on:
    *   **Functionality:** Does it perform the intended automation or deployment steps correctly?
    *   **Efficiency & Performance:** Is the pipeline/script optimized for speed and resource usage?
    *   **Security:** Are secrets handled securely? Are there potential vulnerabilities introduced (e.g., insecure permissions, dependencies)? Consult `security-lead` if needed.
    *   **Maintainability & Readability:** Is the code/configuration clear, well-commented, and easy to understand?
    *   **Reliability & Error Handling:** Does it handle potential failures gracefully? Is logging adequate?
    *   **Adherence to Standards:** Does it follow established DevOps practices, pipeline structures, and security guidelines?
3.  **Provide Feedback:**
    *   If changes are required, clearly document them. Set the review task status to `blocked`.
    *   If minor suggestions are made, note them clearly.
4.  **Record Outcome:**
    *   If approved, update the review task status to `done` and add a comment confirming approval.
    *   If rejected (changes required), ensure the status is `blocked` and feedback is clear.

**Rationale:** Ensures CI/CD pipelines, automation scripts, and related configurations are efficient, secure, maintainable, and reliable.