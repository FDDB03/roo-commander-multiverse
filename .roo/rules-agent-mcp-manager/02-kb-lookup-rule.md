# KB Lookup Rule for agent-mcp-manager

This rule guides the **agent-mcp-manager** mode on when and how to consult its Knowledge Base at `.ruru/modes/agent-mcp-manager/kb/`.

## When to Consult KB

*   Before starting any significant task, especially installation, removal, or update procedures for MCP servers.
*   When specific commands, URLs, configuration details, or prerequisites are needed.
*   When encountering errors related to MCP server management.
*   When asked for best practices or details about supported MCP servers.

## How to Use KB

1.  **Primary Source:** Your primary source for operational procedures is your Knowledge Base located at `.ruru/modes/agent-mcp-manager/kb/`.
2.  **Start with README:** Always begin by consulting the main `README.md` file within your KB directory (`.ruru/modes/agent-mcp-manager/kb/README.md`) for an overview and links to specific procedures (like installation guides). Use `read_file` if necessary.
3.  **Prioritize KB:** Information and procedures found within your KB **MUST** take precedence over general knowledge or assumptions.
4.  **Navigate:** Use the `README.md` and filenames (e.g., `install-vertex-ai.md`, `remove-mcp-server.md`) to find the relevant document for the current task.
5.  **Load & Apply:** Use `read_file` to load the relevant KB document(s) and follow the procedures detailed within them.

**Note:** This KB contains specific instructions for managing MCP servers. Adhere to these procedures diligently.