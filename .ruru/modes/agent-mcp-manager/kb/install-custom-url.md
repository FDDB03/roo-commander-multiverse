# KB Procedure: Install Custom MCP Server from Git URL

## 1. Objective

Install a custom MCP server by cloning its source code from a user-provided Git repository URL, running optional installation commands, and gathering details needed for registration in `.roo/mcp.json`.

## 2. Procedure Steps

1.  **Get Git URL:**
    *   Use `<ask_followup_question>` to ask the user for the full HTTPS or SSH Git repository URL. Provide examples and a cancel option.
    *   Validate the input looks like a Git URL. If invalid or cancelled, stop.
2.  **Determine Target Directory:**
    *   Extract a repository name from the URL (e.g., `my-mcp-server`). Sanitize the name.
    *   Define the target path: `.ruru/mcp-servers/[sanitized-repo-name]`.
3.  **Clone Repository:**
    *   Use `execute_command` to run: `git clone [PROVIDED_URL] [TARGET_DIRECTORY_PATH]`.
    *   Example: `git clone https://github.com/example/my-mcp-server.git .ruru/mcp-servers/my-mcp-server`
    *   If cloning fails, report the error and stop.
4.  **Run Installation Steps (Optional):**
    *   Use `<ask_followup_question>` to ask if installation commands (like `npm install`, `pip install`, `bun install`) are needed within the cloned directory. Provide common examples and a "No installation needed" option.
    *   If commands are provided: Use `execute_command` with the `cwd` parameter set to the target directory to run them. Handle errors.
5.  **Gather Registration Details:**
    *   Inform the user that the code is cloned and installation (if any) is done. State that the server now needs registration in `.roo/mcp.json`, which requires external action (as this agent cannot modify that file directly).
    *   Use `<ask_followup_question>` to ask for:
        *   `server_name`: A unique name for the server entry in `.roo/mcp.json`.
        *   `start_command`: The command to start the server (e.g., `node index.js`, `python main.py`), relative to its directory.
        *   `server_type`: The server type (`stdio` or `sse`).
    *   Provide examples.
6.  **Report for Registration:**
    *   Once details are gathered, use `<attempt_completion>` to report back to the user or coordinator.
    *   Clearly state the gathered details (`server_name`, `start_command`, `server_type`, `target_directory_path`).
    *   Explicitly state that the next step is for an authorized mode/user to update `.roo/mcp.json` with this information.
    *   This procedure ends here.

## 3. Rationale / Notes

*   This procedure handles fetching the code but relies on another entity to perform the final registration in `.roo/mcp.json` due to file access restrictions.
*   Error handling for Git and installation commands is important.
*   The final `.roo/mcp.json` entry needs to correctly combine the `target_directory_path` and the relative `start_command` provided by the user.