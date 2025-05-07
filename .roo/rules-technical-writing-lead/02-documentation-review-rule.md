# Documentation Review Rule for technical-writing-lead

**Rule:** When assigned a task with the tag `review-request` and a title starting with `Review: Docs`, the **technical-writing-lead** mode **MUST** follow this review process:

1.  **Identify Artifact:** Locate the documentation artifact (e.g., README, guide, API docs, user manual section) specified in the task's `required_context`.
2.  **Review Content:** Evaluate the documentation based on:
    *   **Clarity & Conciseness:** Is the language clear, easy to understand, and free of jargon? Is it concise?
    *   **Accuracy:** Is the technical information correct and up-to-date?
    *   **Completeness:** Does it cover the necessary topics adequately for the intended audience? Are there gaps?
    *   **Organization & Structure:** Is the information logically organized with clear headings and structure? Is it easy to navigate?
    *   **Audience Appropriateness:** Is the tone and level of detail suitable for the target audience (e.g., developers, end-users)?
    *   **Grammar & Style:** Is the grammar correct? Does it adhere to the project's style guide (e.g., `.ruru/guides/RURU_STYLE_GUIDE.md`)?
3.  **Provide Feedback:**
    *   If significant revisions are required (e.g., major inaccuracies, structural issues), document them clearly. Set the review task status to `blocked`.
    *   If minor edits (typos, minor clarifications) are needed, note them or potentially make them directly if permissions allow and it's efficient.
4.  **Record Outcome:**
    *   If approved (potentially with minor edits made/suggested), update the review task status to `done` and add a comment confirming approval.
    *   If rejected (major revisions required), ensure the status is `blocked` and feedback is clear.

**Rationale:** Ensures project documentation is clear, accurate, complete, well-organized, and adheres to established standards.