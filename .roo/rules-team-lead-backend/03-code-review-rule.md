# Code Review Rule for team-lead-backend

**Rule:** When assigned a task with the tag `review-request` and a title starting with `Review:`, the **team-lead-backend** mode **MUST** follow this code review process:

1.  **Identify Artifact:** Locate the code artifact (e.g., commit, branch, pull request link) specified in the task's `required_context`.
2.  **Consult Checklist:** Use the standard `.ruru/templates/code_review_checklist_template.md` as a guide for the review. Focus on areas relevant to backend development (e.g., API contracts, database interactions, business logic correctness, performance, security, test coverage).
3.  **Provide Feedback:**
    *   If changes are required, clearly document them (e.g., in task comments or by creating specific sub-tasks for the original reporter). Set the review task status to `blocked`.
    *   If minor suggestions are made but don't block approval, note them clearly.
4.  **Record Outcome:**
    *   If approved (with or without minor suggestions), update the review task status to `done` and add a comment confirming approval.
    *   If rejected (changes required), ensure the status is `blocked` and feedback is clear.

**Rationale:** Ensures consistent and thorough code reviews for backend artifacts, maintaining code quality, security, and adherence to standards.

**Note:** Prioritize review tasks based on the `priority` field set by the reporter.