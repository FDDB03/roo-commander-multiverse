# Global Rules: Task Management

This file contains global rules and guidelines related to task creation, assignment, and communication using the `new_task` tool.

## Task Creation Template Enforcement

**Rule:** The *content* of the task file created by the delegating mode **MUST** conform to the structure defined in the standard task template located at `\.ruru/templates/template-v1.md`. The `new_task` tool itself now takes a JSON reference to this file.
    *   This includes utilizing the suggested emojis within the string values for fields like `status` and `priority` when applicable (e.g., `status = "✅ done"`, `priority = "🔥 High"`), as indicated by the options in the template comments.

**Rationale:** Ensures consistency in task definition across all modes, facilitating better tracking and management, even though the `new_task` message format has changed.

**Template Reference (`.ruru/templates/template-v1.md`):**
```markdown
+++
id = "{TIMESTAMP_ID}" # Placeholder replaced by YYYYMMDDHHMMSS timestamp by delegator
status = "TASK_INITIATED" # Initial status set by delegator. Options: TASK_INITIATED, TASK_RECEIVED, PROCESSING_STARTED, 🛑 blocked, 👀 review, ✅ done, ❌ cancelled
assignee = "{mode-slug}"
reporter_mode = "{current-mode-slug}" # Mode creating the task
tags = ["{tag1}", "{tag2}"]
priority = "Medium"  # Options: 🔥 High, 🔶 Medium, 🟢 Low
# ... other template fields ...
template_version = "1.5" # Example version
+++

# {Task Title} 📌

{Task description…}
```
*(Note: Refer to the actual template file for the complete, up-to-date structure)*

**Example `new_task` Usage (New Flow):**

*Delegating mode first creates the task file (e.g., `\.ruru/tasks/TASK-some-mode-slug-20250508123000.md`) with content conforming to the template, including setting the `id` and initial `status`.*

*Then, the delegating mode uses `new_task` like this:*
```xml
<new_task>
  <mode>some-mode-slug</mode>
  <message>
{
  "task_file_path": "\.ruru/tasks/TASK-some-mode-slug-20250508123000.md",
  "task_id": "20250508123000"
}
  </message>
</new_task>
```

## Task Storage

**Guideline:** Tasks initiated via `<new_task>` **MUST** be persisted as individual files by the *delegating (reporter)* mode *before* the `<new_task>` tool is called. Refer to the [Task Storage Guide](../../../.ruru/guides/TASK_STORAGE_GUIDE.md) for the required file naming convention (`TASK-{AssigneeSlug}-{TaskID}.md`), location (`.ruru/tasks/`), and content structure (based on `\.ruru/templates/template-v1.md`). Task updates (e.g., status changes) are subsequently made to these files by the assigned mode.

**Note:** The successful creation of the task file by the delegating mode is a prerequisite for the task delegation process. See the "Task Persistence and Delegation Guideline" in `\.roo/rules/global/03-mode-behavior-rules.md` for details on the flow and error handling.


## Task Context Requirements

**Guideline:** When creating a task file, the creating mode (`reporter_mode`) **SHOULD**:
1.  Fill in the `required_context` field with essential background information or links (e.g., to relevant KBs, ADRs, previous tasks, specific files).
2.  Clearly define the `expected_outcome` so the assignee understands the goal and completion criteria.
3.  Provide sufficient detail in the main `{Task description…}` section.

**Rationale:** Minimizes ambiguity and reduces the need for the assignee mode to ask clarifying questions, improving efficiency.

## Task Title Naming Convention

**Guideline:** When creating a new task file, the `{Task Title}` within the content should follow the convention:
`{Type}: {Short Description}`

*   `{Type}`: A short prefix indicating the nature of the task (e.g., `Feat`, `Bug`, `Chore`, `Refactor`, `Docs`, `Test`, `Research`, `Spike`). Use PascalCase or a short code.
*   `{Short Description}`: A brief, clear description of the task.

**Examples:**
*   `Feat: Implement user login via email`
*   `Bug: Fix incorrect calculation on dashboard widget`
*   `Chore: Update project dependencies`
*   `Refactor: Extract database logic from controller`
*   `Docs: Add API documentation for /users endpoint`

**Rationale:** Provides quick context about the task type and improves scannability in task lists or boards.

## Subtask Mode Assignment Guideline

**Guideline:** When a mode needs to create a subtask to be handled by another mode:
1.  Consult the `\.ruru/guides/MODE_SELECTION_GUIDE.md` file.
2.  Based on the guide and the nature of the subtask, determine the most appropriate mode slug for the `assignee` field when preparing the task file content.
3.  If unsure, consider using the `orchestrator` mode to delegate the subtask or use `ask_followup_question` to clarify with the user.

**Rationale:** Ensures subtasks are routed to the most suitable specialized mode, improving efficiency and leveraging the multi-mode architecture effectively.

## Task Status & Communication Rule

**Rule:** Modes assigned to a task (after receiving the task file reference via `<new_task>` and reading the file) **MUST**:
1.  **Acknowledge & Update Status:** Update the task file status from `TASK_INITIATED` to `TASK_RECEIVED` or `PROCESSING_STARTED` (using tools like `apply_diff` or `write_to_file`).
2.  **Update Status:** Keep the task `status` field in the file accurate throughout its lifecycle (e.g., `PROCESSING_STARTED`, `🛑 blocked`, `👀 review`, `✅ done`).
3.  **Update Checklists:** If the task description contains Markdown checklists (e.g., under a "Subtasks" or similar heading), update the status of individual checklist items (e.g., changing `[ ]` to `[x]`) as they are completed using `apply_diff` or `write_to_file`. This is in addition to updating the overall task `status` field in the frontmatter.
    *   Example: Change `- [ ] Implement API endpoint` to `- [x] Implement API endpoint` upon completion.
4.  **Report Blockers:** If blocked, update the status to `blocked` and clearly state the blocker in the task file description or comments. Consider creating a new task for the `reporter_mode` or relevant lead to resolve the blocker.
5.  **Request Clarification:** If context in the task file is insufficient, use `ask_followup_question` directed at the `reporter_mode` or create a clarification task.
6.  **Report Completion & Feedback:** Upon completion, update the status to `done` (or `review`) in the task file. Provide feedback to the original `reporter_mode` (e.g., by creating a new task referencing the original `task_id` and outcome).

**Rationale:** Improves visibility into task progress, facilitates proactive blocker resolution, and mimics standard team communication protocols around assigned work, adapted to the file-based task reference flow.