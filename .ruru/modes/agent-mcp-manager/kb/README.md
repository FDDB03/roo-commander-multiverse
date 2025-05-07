# Knowledge Base: 🛠️ MCP Manager Agent

This Knowledge Base contains the specific procedures used by the `agent-mcp-manager` mode to guide users through installing and managing different MCP servers.

## Overview

The agent follows an interactive workflow:
1.  Presents available installation and management options (defined by the files below).
2.  Routes to the specific KB file based on user selection.
3.  Executes the steps within the selected KB file (prerequisite checks, cloning, dependency installation, configuration prompting, `.roo/mcp.json` update).

## KB Files

This directory contains procedures for specific actions:

*   **`README.md`**: This file - provides an overview of the KB.
*   **`check-updates.md`**: Procedure for checking for updates for an installed MCP server.
*   **`install-custom-npm-location.md`**: Procedure for installing an MCP server from a custom local NPM package location.
*   **`install-custom-url.md`**: Procedure for installing a custom MCP server from a Git URL.
*   **`install-vertex-ai.md`**: Procedure for installing the recommended Vertex AI MCP server.
*   **`remove-mcp-server.md`**: Procedure for removing an existing MCP server configuration.

*(Note: Ensure these files contain detailed, step-by-step instructions for the agent to follow, including necessary commands, prompts for user input, and file modifications.)*