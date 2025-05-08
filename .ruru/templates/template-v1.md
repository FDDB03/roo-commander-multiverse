---
id: "{TIMESTAMP_ID}" # Placeholder replaced by YYYYMMDDHHMMSS timestamp by delegator
status: "TASK_INITIATED" # Initial status set by delegator. Options: TASK_INITIATED, TASK_RECEIVED, PROCESSING_STARTED, 🛑 blocked, 👀 review, ✅ done, ❌ cancelled
assignee: "{mode-slug}"
reporter_mode: "{current-mode-slug}" # Mode creating the task
tags:
  - "{tag1}"
  - "{tag2}"
priority: "Medium"  # Options: 🔥 High, 🔶 Medium, 🟢 Low
estimated_effort: "" # Optional: e.g., Small, Medium, Large, T-Shirt Size
story_points: 0 # Optional: Integer value for Agile story points
due_date: "" # Optional: YYYY-MM-DD
epic_link: ""       # Link to related epic/feature task ID or URL
blocking_tasks: [] # Optional: List of task IDs/filenames that block this task
related_tasks: []  # Optional: List of task IDs/filenames related to this task
required_context: "" # Brief description or links to necessary background info ℹ️
expected_outcome: "" # Clear statement of what 'done' looks like for this task 🎯
template_version: "1.6-yaml" # Version indicates YAML format
---

# {Task Title} 📌

{Task description…}

## Subtasks ✅

*   [ ] Subtask 1
*   [ ] Subtask 2