# KB Procedure: Install MCP Server via NPM into Custom Subdirectory

## 1. Objective

Install an NPM-based MCP server package into a dedicated subdirectory (`.ruru/mcp-servers/[server-name]/`) instead of the root `node_modules`, and configure `.roo/mcp.json` accordingly.

**Note:** This is a non-standard approach for organizing server code. Use only if this specific structure is required.

## 2. Procedure Steps

1.  **Create Directories:**
    *   Ensure the base `.ruru/mcp-servers/` directory exists.
    *   Create a server-specific subdirectory: `mkdir -p .ruru/mcp-servers/[server-name]` (replace `[server-name]` appropriately, e.g., `vertex-ai`). Use `execute_command`.
2.  **Install via NPM:**
    *   Use `execute_command` with the `cwd` parameter set to the newly created server subdirectory (`.ruru/mcp-servers/[server-name]`).
    *   Run the NPM install command within that directory: `npm install [mcp-server-package-name] --save-dev` (replace `[mcp-server-package-name]` e.g., `vertex-ai-mcp-server`).
    *   **Important:** Execute `npm install` directly within the subdirectory using the `cwd` parameter; do not chain `cd` and `npm install` from the project root.
3.  **Configure `.roo/mcp.json`:**
    *   Use `read_file` to load `.roo/mcp.json`.
    *   Parse the JSON. Locate or add the entry for `[server-name]`.
    *   **Crucially, set the `args` path** to point to the server's entry point within the custom subdirectory. Example:
        ```json
        "args": [
          "./.ruru/mcp-servers/[server-name]/node_modules/[mcp-server-package-name]/[path/to/entry/point.js]"
          // e.g., "./.ruru/mcp-servers/vertex-ai/node_modules/vertex-ai-mcp-server/build/index.js"
        ]
        ```
    *   Ensure other fields like `command`, `env`, `disabled`, `alwaysAllow`, `timeout` are set correctly.
    *   Use `write_to_file` (or preferably `apply_diff` if modifying existing entries) to save the updated `.roo/mcp.json`. Ensure valid JSON is written.
4.  **Activation:**
    *   Inform the user that a restart or reload of the main application (e.g., Roo Commander) is required to load the updated `.roo/mcp.json` and launch the server from the custom path. Use `<attempt_completion>`.

## 3. Rationale / Notes

*   This method keeps server dependencies isolated within `.ruru/mcp-servers/[server-name]/node_modules/`.
*   Requires careful construction of the `args` path in `.roo/mcp.json`.
*   Requires application restart to take effect.