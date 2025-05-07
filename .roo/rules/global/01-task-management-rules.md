# Global Rules: Task Management

This file contains global rules and guidelines related to task creation, assignment, and communication using the `new_task` tool.

## Task Creation Template Enforcement

**Rule:** When using the `new_task` tool, the `message` parameter **MUST** conform to the structure defined in the standard task template located at `.ruru/templates/template-v1.md`.

**Rationale:** Ensures consistency in task creation across all modes, facilitating better tracking and management.

**Template Reference (`.ruru/templates/template-v1.md`):**
```markdown
+++
id = "{AUTO_INCREMENT}"
status = "pending" # Options: pending, in-progress, blocked, review, done, cancelled
assignee = "{mode-slug}"
reporter_mode = "{current-mode-slug}" # Mode creating the task
tags = ["{tag1}", "{tag2}"]
priority = "Medium"  # Options: High, Medium, Low
epic_link = ""       # Link to related epic/feature task ID or URL
required_context = "" # Brief description or links to necessary background info
expected_outcome = "" # Clear statement of what 'done' looks like for this task
template_version = "1.1" # Incremented version
+++

# {Task Title}

{Task description…}
```

**Example `new_task` Usage:**
```xml
<new_task>
  <mode>some-mode-slug</mode>
  <message>
+++
id = "{AUTO_INCREMENT}"
status = "pending"
assignee = "some-mode-slug"
reporter_mode = "architect"
tags = ["backend", "refactor"]
priority = "High"
epic_link = "URL_to_epic"
required_context = "See ADR-005 for background on service boundaries."
expected_outcome = "Authentication logic is extracted into a separate service."
template_version = "1.1"
+++

# Refactor: Authentication Service

Detailed description of the refactoring task goes here...
  </message>
</new_task>
```

## Task Storage

**Guideline:** Tasks created via `<new_task>` should ideally be persisted as individual files. Refer to the [Task Storage Guide](../../../.ruru/guides/TASK_STORAGE_GUIDE.md) for the intended file naming convention, location (`.ruru/tasks/`), and content structure. Task updates should modify these files.

**Note:** The automatic creation and updating of these task files may depend on system capabilities.


## Task Context Requirements

**Guideline:** When creating a task for another mode, the creating mode (`reporter_mode`) **SHOULD**:
1.  Fill in the `required_context` field with essential background information or links (e.g., to relevant KBs, ADRs, previous tasks, specific files).
2.  Clearly define the `expected_outcome` so the assignee understands the goal and completion criteria.
3.  Provide sufficient detail in the main `{Task description…}` section.

**Rationale:** Minimizes ambiguity and reduces the need for the assignee mode to ask clarifying questions, improving efficiency.

## Task Title Naming Convention

**Guideline:** When creating a new task using the `new_task` tool, the `{Task Title}` within the message template should follow the convention:
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

**Guideline:** When a mode needs to create a subtask to be handled by another mode (using the `new_task` tool):
1.  Consult the `.ruru/guides/MODE_SELECTION_GUIDE.md` file.
2.  Based on the guide and the nature of the subtask, determine the most appropriate mode slug for the `assignee` field in the task template.
3.  If unsure, consider using the `orchestrator` mode to delegate the subtask or use `ask_followup_question` to clarify with the user.

**Rationale:** Ensures subtasks are routed to the most suitable specialized mode, improving efficiency and leveraging the multi-mode architecture effectively.

## Task Status & Communication Rule

**Rule:** Modes assigned to a task **MUST**:
1.  **Acknowledge:** (Optional, depending on system capability) Indicate acceptance or start of work, potentially by updating the task status to `in-progress`.
2.  **Update Status:** Keep the task `status` field accurate (e.g., `in-progress`, `blocked`, `review`, `done`).
3.  **Report Blockers:** If blocked, update the status to `blocked` and clearly state the blocker in the task description or comments (if a comment mechanism exists). Consider creating a new task for the `reporter_mode` or relevant lead to resolve the blocker.
4.  **Request Clarification:** If context is insufficient, use `ask_followup_question` directed at the `reporter_mode` or create a clarification task.
5.  **Report Completion:** Upon completion, update the status to `done` (or `review` if applicable) and provide a summary of the outcome.

**Rationale:** Improves visibility into task progress, facilitates proactive blocker resolution, and mimics standard team communication protocols around assigned work.