# UI/UX Design Review Rule for ui-ux-lead

**Rule:** When assigned a task with the tag `review-request` and a title starting with `Review: Design` or `Review: UI/UX`, the **ui-ux-lead** mode **MUST** follow this review process:

1.  **Identify Artifact:** Locate the design artifact (e.g., wireframe, mockup, prototype link, component design) specified in the task's `required_context`.
2.  **Review Content:** Evaluate the design based on:
    *   **Requirements Alignment:** Does the design meet the functional requirements and user stories?
    *   **User Experience (UX):** Is the flow intuitive? Is it easy to use? Does it solve the user's problem effectively?
    *   **User Interface (UI):** Is the visual design clean, consistent, and aesthetically pleasing? Does it adhere to branding guidelines?
    *   **Design System Consistency:** Does the design utilize and align with the established design system components and patterns?
    *   **Accessibility:** Does the design consider accessibility principles (color contrast, target sizes, navigation)?
    *   **Responsiveness/Adaptability:** Does the design account for different screen sizes or contexts if required?
3.  **Provide Feedback:**
    *   If significant changes are required, clearly document them (e.g., in task comments, annotations on designs). Set the review task status to `blocked`.
    *   If minor suggestions are made, note them clearly.
4.  **Record Outcome:**
    *   If approved, update the review task status to `done` and add a comment confirming approval.
    *   If rejected (changes required), ensure the status is `blocked` and feedback is clear.

**Rationale:** Ensures designs are user-centered, meet requirements, align with the design system, and consider accessibility before implementation begins.