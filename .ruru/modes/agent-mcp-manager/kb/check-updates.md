# KB Procedure: Check for MCP Server Updates

## 1. Objective

Check installed MCP servers (defined in `.roo/mcp.json` and likely residing in `.ruru/mcp-servers/`) for available updates, typically by checking their Git repository status.

## 2. Procedure Steps

**(Note: This procedure assumes servers were installed via Git and are located in `.ruru/mcp-servers/<server-name>`.)**

1.  **Read Configuration:** Use `read_file` to load `.roo/mcp.json`.
2.  **Identify Servers:** Parse the JSON to identify installed servers. Focus on servers that have associated Git repository information or follow the expected directory structure.
3.  **Iterate and Check:** For each relevant server:
    *   Determine its local directory (e.g., `.ruru/mcp-servers/<server-name>`). Verify the directory exists.
    *   Use `execute_command` with the `cwd` parameter set to the server's directory to run `git fetch origin`. Handle potential errors (e.g., not a git repo, no remote).
    *   Use `execute_command` (again with `cwd`) to run `git status -uno`. Analyze the output to determine if the local branch is behind the remote (`origin/main` or `origin/master` typically).
    *   Record the update status (e.g., "Up-to-date", "Updates available", "Check failed").
4.  **Report Findings:** Present a summary of servers checked and their update status to the user using `<attempt_completion>`. If updates are found, you might suggest triggering a separate update procedure (e.g., "Updates found for 'vertex-ai'. Would you like to attempt an update?").

## 3. Rationale / Notes

*   Error handling for file reading and Git commands is crucial.
*   The exact `git status` or `git log` command might need adjustment based on common branch naming conventions (`main` vs. `master`).
*   Applying updates (e.g., `git pull`) should be handled by a separate KB procedure, triggered after user confirmation.