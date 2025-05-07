# Security Review Rule for security-lead

**Rule:** When assigned a task with the tag `review-request` and a title starting with `Review: Security`, or when consulted on security implications, the **security-lead** mode **MUST** follow this review process:

1.  **Identify Artifact/Context:** Locate the artifact (e.g., code change, ADR, design document, infrastructure change) or understand the context specified in the task's `required_context`.
2.  **Review Content:** Evaluate the artifact/change based on potential security risks and adherence to best practices:
    *   **Vulnerability Identification:** Check for common vulnerabilities (OWASP Top 10, etc.) relevant to the artifact type (e.g., injection flaws, broken authentication, misconfigurations, insecure dependencies).
    *   **Secure Design Principles:** Assess alignment with principles like least privilege, defense in depth, secure defaults.
    *   **Data Handling:** Verify secure handling of sensitive data (encryption, masking, storage).
    *   **Authentication/Authorization:** Check for proper implementation and enforcement.
    *   **Logging & Monitoring:** Ensure security-relevant events are logged appropriately without exposing sensitive info.
    *   **Compliance:** Consider relevant compliance requirements (if applicable).
    *   **(Optional):** Use security scanning tools if appropriate and available via `execute_command`.
3.  **Provide Feedback:**
    *   If security risks or significant deviations from best practices are found, clearly document them with recommended mitigations. Set the review task status to `blocked`.
    *   If minor suggestions or hardening opportunities are identified, note them clearly.
4.  **Record Outcome:**
    *   If approved (no major risks found), update the review task status to `done` and add a comment confirming approval (potentially noting minor suggestions).
    *   If rejected (risks identified), ensure the status is `blocked` and feedback/mitigation steps are clear.

**Rationale:** Ensures security considerations are integrated into the development lifecycle, reducing vulnerabilities and promoting secure design.