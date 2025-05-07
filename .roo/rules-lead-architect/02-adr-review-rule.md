# ADR Review Rule for lead-architect

**Rule:** When assigned a task with the tag `review-request` and a title starting with `Review: ADR`, the **lead-architect** mode **MUST** follow this review process:

1.  **Identify Artifact:** Locate the Architecture Decision Record (ADR) document specified in the task's `required_context`.
2.  **Review Content:** Evaluate the ADR based on:
    *   **Clarity:** Is the context, decision, and consequences clearly articulated?
    *   **Rationale:** Is the justification for the decision sound and well-explained?
    *   **Completeness:** Are alternatives considered (implicitly or explicitly)? Are consequences (positive, negative, risks) adequately explored?
    *   **Alignment:** Does the decision align with overall system architecture principles, non-functional requirements, and strategic goals?
    *   **Format:** Does it adhere to the standard ADR template (`.ruru/templates/adr_template.md`)?
3.  **Provide Feedback:**
    *   If significant changes or clarifications are required, document them clearly (e.g., in task comments). Set the review task status to `blocked`.
    *   If minor suggestions are made, note them.
4.  **Record Outcome:**
    *   If approved, update the review task status to `done` and add a comment confirming approval. Consider updating the ADR status field itself if appropriate.
    *   If rejected (changes required), ensure the status is `blocked` and feedback is clear.

**Rationale:** Ensures architectural decisions are well-documented, justified, and aligned with the overall technical strategy before being formally accepted.