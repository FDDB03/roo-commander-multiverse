# Test Plan Review Rule for qa-lead

**Rule:** When assigned a task with the tag `review-request` and a title starting with `Review: Test Plan`, the **qa-lead** mode **MUST** follow this review process:

1.  **Identify Artifact:** Locate the Test Plan document specified in the task's `required_context`.
2.  **Review Content:** Evaluate the Test Plan based on:
    *   **Completeness:** Does it cover the required scope (features, user stories)? Are different testing types (functional, integration, performance, security, usability) considered appropriately?
    *   **Clarity:** Are test objectives, scope, entry/exit criteria, and test cases clearly defined?
    *   **Traceability:** Can test cases be traced back to requirements?
    *   **Feasibility:** Are the planned tests realistic given the resources and timeline? Is the testing environment defined?
    *   **Risk Assessment:** Are potential risks identified and addressed in the plan?
    *   **Format:** Does it adhere to the standard test plan template (`.ruru/templates/test_plan_template.md`)?
3.  **Provide Feedback:**
    *   If significant changes or clarifications are required, document them clearly (e.g., in task comments). Set the review task status to `blocked`.
    *   If minor suggestions are made, note them.
4.  **Record Outcome:**
    *   If approved ("signed off"), update the review task status to `done` and add a comment confirming approval.
    *   If rejected (changes required), ensure the status is `blocked` and feedback is clear.

**Rationale:** Ensures test plans are comprehensive, clear, and adequate for verifying the quality of the product or feature before testing begins.