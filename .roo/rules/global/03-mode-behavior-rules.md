# Global Rules: Mode Behavior

This file contains global rules and guidelines related to general mode operation, error handling, and interaction patterns.

## Default Error Handling Protocol

**Guideline:** If a tool use results in an error:
1.  Analyze the error message provided in the user's response.
2.  If the error is recoverable (e.g., file not found but can be created, incorrect parameter value that can be corrected), attempt to retry the tool use with the necessary corrections.
3.  If the error is persistent or indicates a deeper issue, consider using a different tool or approach.
4.  If unsure how to proceed, use the `ask_followup_question` tool to clarify the issue or ask for guidance.
5.  Log the error and the resolution attempt in the project journal if appropriate.

**Rationale:** Provides a consistent approach to handling tool failures, promoting resilience and problem-solving.

## Project Journaling Guideline

**Guideline:** Modes should consider adding entries to the project journal (`.ruru/journal/journal.md`) for significant events, decisions, or outcomes. This includes:
*   Completion of major tasks or milestones.
*   Key architectural or strategic decisions made.
*   Significant errors encountered and their resolution.
*   Important user feedback received.
*   Mode switches with significant context transfer.

See the [Project Journaling Guide](../../../.ruru/guides/JOURNALING_GUIDE.md) for more details and best practices.

**Format:** Use the established header format: `## YYYY-MM-DD HH:MM - {Author/Mode} - {Summary}`

**Rationale:** Maintains a persistent log of project progress and key decisions for traceability and context sharing.

## Knowledge Base Maintenance Guideline

**Guideline:** Modes, particularly those designated as owners of specific KBs (see main `README.md`), should strive to keep their knowledge bases (`.ruru/modes/<mode-slug>/kb/`) accurate and up-to-date.
*   After making significant decisions (e.g., architectural choices documented in ADRs), implementing new standard processes, or discovering important best practices, consider updating the relevant KB(s).
*   If creating new reusable scripts, configurations, or documentation, add references or summaries to the appropriate KB.
*   Periodically review KB content for staleness or inaccuracies.

**Rationale:** Ensures the KBs remain reliable sources of truth for all modes, promoting consistency and preserving project knowledge.


## Security Consideration Reminder

**Guideline:** Before writing code, modifying infrastructure, or handling sensitive data, modes should briefly consider potential security implications.
*   Does this change introduce new vulnerabilities?
*   Are appropriate access controls in place?
*   Is sensitive data being handled securely?
*   Consult the `security-lead` mode or its KB if significant security concerns arise.

**Rationale:** Promotes a security-aware mindset across all modes, aligning with DevSecOps principles.

## Version Control Guideline

**Guideline:** Modes performing actions that modify version-controlled files (code, configuration, documentation) **SHOULD** adhere to the project's established version control practices.
*   Consult the [Git Workflow Guide](../../../.ruru/guides/GIT_WORKFLOW_GUIDE.md) for standard procedures.
*   Refer to mode-specific KBs or rules for any specialized version control instructions.
*   Use `execute_command` for Git operations when applicable.

**Rationale:** Ensures consistency, traceability, and collaboration through proper use of version control.


## Mode Switching Guideline

**Guideline:** Use the `switch_mode` tool when the current mode's specialization is no longer the best fit for the immediate next steps of the task.
*   Provide a clear `reason` for the switch.
*   Ensure necessary context is available or transferred for the target mode.
*   Prefer completing related sub-tasks within the current mode if efficient, rather than switching excessively.

**Rationale:** Encourages thoughtful use of specialized modes while minimizing unnecessary overhead from frequent context switching.

## Review Request Guideline

**Guideline:** When a mode requires an artifact (e.g., code, document, design) to be reviewed or approved by another mode:
1.  Create a new task using the `new_task` tool and the standard template (`.ruru/templates/template-v1.md`).
2.  Set the `assignee` field to the slug of the appropriate reviewing mode (e.g., `team-lead-frontend`, `lead-architect`, `qa-lead`).
3.  Prefix the task `{Task Title}` with `Review:` (e.g., `Review: User Login Component`).
4.  Include the tag `review-request` in the `tags` array.
5.  In the `required_context` field, provide clear links or paths to the specific artifact(s) needing review.
6.  In the `expected_outcome` field, state what constitutes a successful review (e.g., "Code approved for merge", "ADR accepted", "Test plan signed off").

**Rationale:** Establishes a standard process for requesting reviews, ensuring clarity for the reviewer and trackability of the review process.


## Task Persistence Guideline (Assignee Saves - Workaround)

**Guideline:** Due to current system limitations where tasks created via `<new_task>` are not automatically saved by the system and the auto-generated ID is not consistently returned or usable for immediate file naming, the mode *assigned* a new task (the `assignee`) **MUST** manually save the received task message payload to a file as one of its initial actions upon receiving the task.

**Procedure:**

1.  Upon receiving a new task message payload (e.g., from the system after another mode used `<new_task>`):
2.  Identify its own mode slug (this will be the `{assignee_slug}` for the filename).
3.  Generate a current timestamp string in `YYYYMMDDHHMMSS` format (let's call this `timestamp_str`).
4.  Construct the filename: `.ruru/tasks/TASK-{assignee_slug}-{timestamp_str}.md` (replace `{assignee_slug}` with the mode's own slug and `{timestamp_str}` with the generated timestamp).
5.  Take the received task message payload.
6.  Replace any placeholder `id` (e.g., `"{AUTO_INCREMENT}"`, `"{TIMESTAMP_ID}"`) within the payload's frontmatter with the generated `timestamp_str`.
7.  Use the `<write_to_file>` tool to save the *modified* task message payload to the constructed filename. The `<write_to_file>` tool will create the `.ruru/tasks/` directory if it doesn't exist.

**Rationale:** Ensures task persistence despite the lack of automatic system saving, providing a record of received and assigned work with a unique filename and a corresponding unique ID within the file content. This is a workaround until the system implements automatic task saving with ID-based naming as described in the `TASK_STORAGE_GUIDE.md`. The responsibility for saving is placed on the assignee to ensure the task is recorded before work commences by the responsible mode.


## Mode-Specific Rule Naming Convention

**Guideline:** Files containing rules specific to a single mode, located within the `.roo/rules-<mode-slug>/` directories, should follow the naming convention:
`NN-<short-description>-rule.md`

*   `NN`: A two-digit sequence number (e.g., `01`, `02`, `10`) indicating the order or priority of the rule within that mode's ruleset.
*   `<short-description>`: A brief, hyphenated description of the rule's purpose (e.g., `kb-lookup`, `file-access-policy`).
*   `-rule.md`: The literal suffix.

**Example:**
*   `.roo/rules-code/01-linting-check-rule.md`
*   `.roo/rules-architect/02-adr-template-rule.md`

**Rationale:** Provides a consistent and predictable structure for mode-specific rules, making them easier to find, manage, and understand their intended order.