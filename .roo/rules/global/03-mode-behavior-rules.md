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


## Task Persistence and Delegation Guideline

**Guideline:** This guideline outlines the process for creating, delegating, and persisting tasks initiated via the `<new_task>` tool. The *delegating (reporter)* mode is responsible for creating the physical task file.

**Procedure:**

**A. Delegating (Reporter) Mode Responsibilities:**

1.  **Prepare Task Content:**
    *   Fetch the standard task template (e.g., from `\.ruru/templates/template-v1.md`).
    *   Populate all necessary fields, including `assignee` (the target mode slug) and `reporter_mode` (its own slug).
    *   Set the initial `status` in the task content to `TASK_INITIATED` (or an equivalent status indicating creation by the delegator).

2.  **Generate Unique Task ID:**
    *   Create a `YYYYMMDDHHMMSS` timestamp string. This timestamp will serve as the unique `TaskID`.

3.  **Update Task Content with ID:**
    *   In the prepared task content, replace the placeholder for `id` (e.g., `"{TIMESTAMP_ID}"` or `"{AUTO_INCREMENT}"`) with the generated `TaskID`.

4.  **Construct Filename:**
    *   The standard filename convention is: `\.ruru/tasks/TASK-{AssigneeSlug}-{TaskID}.md`.
        *   Example: `\.ruru/tasks/TASK-agent-mcp-manager-20250508120000.md`.

5.  **Write Task File:**
    *   Use the `<write_to_file>` tool to save the fully prepared task content (with the `TaskID` embedded) to the constructed file path.
    *   **Error Handling:**
        *   If `<write_to_file>` fails, log the error. Attempt a limited number of retries (e.g., 2) for transient issues.
        *   If retries fail, the delegation process for this task must halt. Log this critical failure.

6.  **Delegate Task via `<new_task>`:**
    *   Only proceed if the task file was successfully written.
    *   The `mode` parameter of `<new_task>` should be the `AssigneeSlug`.
    *   The `message` parameter should be a JSON object containing a reference to the task file and the TaskID:
        ```json
        {
          "task_file_path": "\.ruru/tasks/TASK-{AssigneeSlug}-{TaskID}.md",
          "task_id": "{TaskID}"
        }
        ```
    *   **Error Handling:**
        *   If `<new_task>` fails, log the error. Attempt limited retries.
        *   If `<new_task>` fails persistently *after* the task file was successfully written, this creates an orphaned task file. Log this critical inconsistency.

**B. Assignee Mode Responsibilities:**

1.  **Receive Task Reference:**
    *   The assignee mode will receive the JSON message from the `<new_task>` tool.
    *   Parse the `task_file_path` and `task_id` from the message.
    *   Validate the received JSON structure. If malformed, log an error and consider notifying the delegator (e.g., by creating a new task back to the `reporter_mode` specified in the original, if accessible, or logging for manual review).

2.  **Read Task File:**
    *   Use the `<read_file>` tool to read the content of the task file specified by `task_file_path`.
    *   **Error Handling:** If `<read_file>` fails (e.g., file not found, permission issues), log a critical error. The task cannot be processed. Notify the delegator if a mechanism exists.

3.  **Idempotency Check:**
    *   Using the `task_id` from the message (which should also match the `id` field within the task file), check if this task has already been processed or is currently in progress. (Mechanism: e.g., maintain a local log/cache of processed TaskIDs, or check for specific status markers in the task file if it's updated reliably).
    *   If the task is a duplicate and already completed or in a terminal state, log this, acknowledge if necessary, and do not reprocess.
    *   If it's a duplicate and still in an active state (e.g. `PROCESSING_STARTED`), the mode should decide based on its capabilities whether to resume or report an issue.

4.  **Update Task Status (Initial):**
    *   If the task is new and valid, update the `status` field within the task file (e.g., from `TASK_INITIATED` to `TASK_RECEIVED` or `PROCESSING_STARTED`) using `<apply_diff>` or `<write_to_file>` (with full content).

5.  **Process Task:**
    *   Execute the task as described in its content. Validate task content against expected structure/schema if possible.

6.  **Update Task Status (Final) & Provide Feedback:**
    *   Upon completion or failure, update the `status` in the task file (e.g., `TASK_COMPLETED`, `TASK_FAILED`).
    *   Provide feedback to the delegator (e.g., by creating a new task for the original `reporter_mode`, referencing the `task_id` and outcome).

**Rationale:** This revised process shifts task file creation to the delegating mode, ensuring the file exists before delegation. It introduces unique TaskIDs (timestamps) for better tracking and idempotency, clarifies the `<new_task>` message format, and incorporates foundational error handling and state management steps. This provides a more robust and traceable task delegation workflow.


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

# Reminder: Instructions for Tool Use

Tool uses are formatted using XML-style tags. The tool name is enclosed in opening and closing tags, and each parameter is similarly enclosed within its own set of tags. Here's the structure:

<tool_name>
<parameter1_name>value1</parameter1_name>
<parameter2_name>value2</parameter2_name>
...
</tool_name>

For example:

<attempt_completion>
<result>
I have completed the task...
</result>
</attempt_completion>

Always adhere to this format for all tool uses to ensure proper parsing and execution.