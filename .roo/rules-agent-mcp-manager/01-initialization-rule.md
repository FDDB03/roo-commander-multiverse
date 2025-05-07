# Initialization Rule for agent-mcp-manager

This rule defines how the **agent-mcp-manager** mode handles the initial user interaction upon activation.

## Procedure

1.  **Present Main Menu:**
    *   Use the `<ask_follow_up_question>` tool to present the main options for MCP server management.
    *   **Tool Call:**
        ```xml
        <ask_follow_up_question>
         <question>Welcome to the MCP Manager Agent! How can I assist you with MCP servers today?</question>
         <follow_up>
           <suggest>🔌 Install Vertex AI Server</suggest>
           <suggest>🌐 Install Custom Server from URL</suggest>
           <suggest>📚 Install Other MCP Servers...</suggest>
           <suggest>️ Remove an existing MCP Server</suggest>
           <suggest>🔄 Check for MCP Server Updates</suggest>
           <suggest>❌ Cancel</suggest>
         </follow_up>
        </ask_follow_up_question>
        ```
2.  **Process User Selection:**
    *   Based on the user's response, determine the selected action.
    *   **Route to KB Procedure:**
        *   If "Install Vertex AI": Follow `.ruru/modes/agent-mcp-manager/kb/install-vertex-ai.md`.
        *   If "Install Unsplash": Follow `.ruru/modes/agent-mcp-manager/kb/install-unsplash.md`.
        *   If "Install Custom URL": Follow `.ruru/modes/agent-mcp-manager/kb/install-custom-url.md`.
        *   If "Install Other": Proceed to list other `install-*.md` files from the KB and present a sub-menu (See Step 3).
        *   If "Remove Server": Follow `.ruru/modes/agent-mcp-manager/kb/remove-mcp-server.md`.
        *   If "Check Updates": Follow `.ruru/modes/agent-mcp-manager/kb/check-updates.md`.
        *   If "Cancel": Use `<attempt_completion>` to report cancellation and stop.
        *   If Unmatched: Re-present the main menu (Step 1).
3.  **Handle "Other Servers" Sub-Menu (If selected):**
    *   Use `<list_files>` on `.ruru/modes/agent-mcp-manager/kb/`.
    *   Filter for `install-*.md` files (excluding main menu items).
    *   Generate and present a sub-menu using `<ask_follow_up_question>` with options like "Install [Server Name] Server", "Back to Main Menu", "Cancel".
    *   Process the sub-menu selection:
        *   If "Install [Server Name]": Follow the corresponding `install-[server-name].md` KB file.
        *   If "Back to Main Menu": Return to Step 1.
        *   If "Cancel": Use `<attempt_completion>` to report cancellation and stop.
        *   If Unmatched: Re-present the sub-menu.
4.  **Execute KB Procedure:** Once a specific KB file is identified, follow the procedure detailed within that file. This rule's execution ends, and the linked KB procedure takes over.

**Note:** This rule orchestrates the initial menu navigation, delegating the actual work to procedures defined in the Knowledge Base (`.ruru/modes/agent-mcp-manager/kb/`).