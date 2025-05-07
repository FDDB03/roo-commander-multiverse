# KB Procedure: Remove MCP Server

## 1. Objective

Safely remove an installed MCP server by deleting its directory and removing its configuration entry from `.roo/mcp.json` after user confirmation.

## 2. Procedure Steps

1.  **Read Configuration & List Servers:**
    *   Use `read_file` to load `.roo/mcp.json`. Handle potential errors (file not found, invalid JSON).
    *   Parse the JSON and extract the server names (keys) from the `mcpServers` object.
    *   If no servers are found, report "No MCP servers are currently configured for removal." using `<attempt_completion>` and stop.
2.  **Prompt User for Selection:**
    *   Use `ask_followup_question` to ask "Which MCP server would you like to remove?".
    *   Provide a `<suggest>` tag for each server name found, plus a `<suggest>Cancel Removal</suggest>` option.
    *   Store the selected `server_to_remove`. If cancelled, report and stop.
3.  **Confirm Removal:**
    *   Use `ask_followup_question` to ask: "Are you sure you want to permanently remove the '{{server_to_remove}}' MCP server? This will delete its files in `.ruru/mcp-servers/` and its entry in `.roo/mcp.json`." (Substitute the actual server name).
    *   Provide suggestions: "Yes, remove {{server_to_remove}}" and "No, cancel removal".
    *   If the user cancels, report and stop.
4.  **Delete Server Directory:**
    *   Define `target_dir`: `.ruru/mcp-servers/{{server_to_remove}}` (Substitute the actual server name).
    *   Inform the user: "Attempting to delete server directory: {{target_dir}}..."
    *   Use `execute_command`: `rmdir /s /q "{{target_dir}}"` (Using Windows command with quotes for safety).
    *   Log any errors from the command execution (e.g., "Warning: Failed to delete directory...") but proceed.
5.  **Update MCP Configuration (`.roo/mcp.json`):**
    *   Inform the user: "Removing '{{server_to_remove}}' from `.roo/mcp.json`..."
    *   Using the parsed JSON data from Step 1 (or re-read if needed), check if the key `{{server_to_remove}}` exists in the `mcpServers` object.
    *   If it exists, delete the key `{{server_to_remove}}` and its associated value from the `mcpServers` object.
    *   If it doesn't exist, note this ("Server entry already absent.") but continue.
    *   Use `write_to_file` to save the modified JSON object back to `.roo/mcp.json`. Ensure proper JSON formatting (e.g., indent with 2 spaces).
    *   Verify the write operation succeeded. If it fails, report the error and stop.
6.  **Report Completion:**
    *   Use `attempt_completion`: "Successfully removed the '{{server_to_remove}}' MCP server configuration. Directory removal status logged. You may need to reload extensions or restart the application if the server was running."

## 3. Rationale / Notes

*   Includes user confirmation for safety.
*   Attempts to remove both files and configuration.
*   Uses the correct Windows command (`rmdir /s /q`) for directory removal.
*   Assumes the agent has write permission for `.roo/mcp.json`.