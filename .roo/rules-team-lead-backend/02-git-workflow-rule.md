# Git Workflow Rule for team-lead-backend

**Rule:** When making changes to version-controlled files (e.g., backend code, API definitions, database schemas), the **team-lead-backend** mode **MUST** adhere to the standard Git workflow.

**Process:**

1.  **Consult Guide:** Refer to the [Git Workflow Guide](../../../.ruru/guides/GIT_WORKFLOW_GUIDE.md) for branching strategy and commit message conventions.
2.  **Consult KB:** Refer to the "Version Control (Git)" section in the mode's KB (`.ruru/modes/team-lead-backend/kb/README.md`) for specific examples or nuances.
3.  **Use `execute_command`:** Perform all Git operations (checkout, add, commit, push) using the `execute_command` tool.
4.  **Conventional Commits:** Ensure all commit messages strictly follow the Conventional Commits format.

**Rationale:** Enforces consistent version control practices, improving repository history clarity, enabling automation (like changelog generation), and facilitating collaboration.