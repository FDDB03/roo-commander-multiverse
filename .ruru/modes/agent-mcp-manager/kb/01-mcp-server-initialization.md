# KB: MCP Server Initialization Process

This document details the enhanced initialization process for MCP (Model Context Protocol) servers, managed by the `agent-mcp-manager` mode. This process ensures robust startup, especially for Node.js-based servers.

## 1. Server Discovery

*   The `agent-mcp-manager` discovers available MCP servers by reading the [`.roo/mcp.json`](../../../../.roo/mcp.json) configuration file.
*   This file contains an array of server definitions, each specifying how to start and manage a particular MCP server.

## 2. Configuration Validation

For each server entry in [`.roo/mcp.json`](../../../../.roo/mcp.json):
*   **Command Validation:** The `command` field (e.g., "node", "python") must be present and not empty.
*   **Arguments Validation:** The `args` array, specifically the first argument which typically represents the server script path, must be present and the script path itself must not be empty.
*   **Logging:**
    *   If `command` or the script path in `args` is invalid or missing, an error is logged.
    *   The server with invalid configuration is skipped, and initialization for that server is aborted.

## 3. Node.js Server Special Handling

If a server's directory (e.g., [`.ruru/mcp-servers/some-server/`](../../../../.ruru/mcp-servers/some-server/)) contains a [`package.json`](../../../../.ruru/mcp-servers/vertex-ai/package.json) file, it is identified as a Node.js project, and the following steps are performed:

### 3.1. Dependency and Script Checks

*   **`node_modules` Check:** The manager checks for the existence of the `node_modules` subdirectory within the server's directory.
    *   *Log:* "Checking for node_modules directory in [server_path]..."
*   **Server Script Check:** The manager verifies the existence of the server script file, as specified by the first argument in the `args` array from [`.roo/mcp.json`](../../../../.roo/mcp.json).
    *   *Log:* "Checking for server script [script_path]..."

### 3.2. Automated Dependency Installation

*   **Condition:** If the `node_modules` directory is missing OR the server script file is not found.
*   **Action:**
    1.  *Log:* "Missing dependencies or server script for [server_name]. Attempting to install dependencies via npm install..."
    2.  The command `npm install` is executed in the server's root directory (e.g., `cd .ruru/mcp-servers/vertex-ai && npm install`).
    3.  *Log:* The outcome of the `npm install` command (success or failure, including any error messages) is logged.
*   **Post-Installation Check:**
    *   If `npm install` was successful, the server script's existence is re-verified.
    *   *Log:* "Re-verifying server script [script_path] after npm install..."

### 3.3. Error Handling for Node.js Servers

*   If `npm install` fails:
    *   *Log:* "npm install failed for [server_name]. Error: [error_message]."
    *   The server is marked as "failed to initialize."
*   If the server script is still missing after a successful `npm install`:
    *   *Log:* "Server script [script_path] still not found after npm install for [server_name]."
    *   The server is marked as "failed to initialize."

## 4. General Logging

Throughout the initialization process for all server types:
*   Successful validation steps are logged.
*   Intentions to perform actions (e.g., "Attempting to start server [server_name]...") are logged.
*   The success or failure of starting each server is logged.
*   Any errors encountered during the startup of a server are logged.

## 5. Basic Troubleshooting

*   **"Command not found" or "Script not found" errors:**
    *   Verify the `command` and `args` (script path) in [`.roo/mcp.json`](../../../../.roo/mcp.json) are correct for the server.
    *   Ensure the specified executable (e.g., `node`, `python`) is in the system's PATH.
    *   For Node.js servers, check the server's directory for the script file.
*   **Node.js server fails, "npm install failed":**
    *   Check the logs for specific error messages from `npm install`.
    *   Ensure `npm` is installed and accessible in the system's PATH.
    *   Manually navigate to the server's directory (e.g., [`.ruru/mcp-servers/vertex-ai/`](../../../../.ruru/mcp-servers/vertex-ai/)) and try running `npm install` to see detailed errors.
    *   Check the [`package.json`](../../../../.ruru/mcp-servers/vertex-ai/package.json) for valid dependencies.
*   **Server starts but is unresponsive:**
    *   Check the server's own logs (if it produces any) for runtime errors.
    *   Ensure the port specified in [`.roo/mcp.json`](../../../../.roo/mcp.json) (if applicable for remote servers) is not already in use.