# Platform Review Rule for team-lead-platform

**Rule:** When assigned a task with the tag `review-request` and a title starting with `Review: Platform`, the **team-lead-platform** mode **MUST** follow this review process:

1.  **Identify Artifact:** Locate the platform artifact (e.g., IaC code, configuration file, script, diagram link) specified in the task's `required_context`.
2.  **Review Content:** Evaluate the artifact based on:
    *   **Correctness & Functionality:** Does it achieve its intended purpose?
    *   **Adherence to Standards:** Does it follow platform architecture, IaC best practices, security guidelines, and coding standards?
    *   **Maintainability & Readability:** Is the code/configuration clear and easy to maintain?
    *   **Reliability & Scalability:** Are potential impacts on platform stability considered?
    *   **Documentation:** Is the change adequately documented?
3.  **Provide Feedback:**
    *   If changes are required, clearly document them (e.g., in task comments or by creating specific sub-tasks). Set the review task status to `blocked`.
    *   If minor suggestions are made, note them clearly.
4.  **Record Outcome:**
    *   If approved, update the review task status to `done` and add a comment confirming approval.
    *   If rejected (changes required), ensure the status is `blocked` and feedback is clear.

**Rationale:** Ensures platform changes are consistent, maintainable, secure, and adhere to architectural standards.