# Project Configuration Structure (`.roo` and `.ruru`)

This document provides an overview of the configuration directories (`.roo`, `.ruru`) and the custom mode definition file (`.roomodes`) used in this project.

## `.roo` Directory

This directory contains rules that govern the behavior of different modes (agents) within the system.

*   **`rules/`**: Contains global rules (`global-rules.md`) that apply to all modes unless overridden.
*   **`rules-<mode-slug>/`**: Contains rules specific to a particular mode (e.g., `rules-code/`, `rules-architect/`). These rules can refine or override global rules for that specific mode.

## `.ruru` Directory

This directory serves as a central repository for resources, artifacts, guides, and other supporting materials used by the modes.

*   **`artifacts/`**: Stores generated documents, plans, reports, etc., created during project tasks (e.g., ADRs, test plans). Follows naming convention `DocumentType-Identifier.ext`.
*   **`guides/`**: Contains markdown guides explaining project conventions, processes, or tool usage (e.g., `MODE_SELECTION_GUIDE.md`, `CONTRIBUTING_RULES_TEMPLATES.md`, `RURU_STYLE_GUIDE.md`).
*   **`journal/`**: Holds the project journal (`journal.md`), a chronological log of significant events, decisions, and outcomes.
*   **`mcp-servers/`**: Contains configurations or code related to Model Context Protocol (MCP) servers, if used.
*   **`modes/`**: Contains mode-specific resources, primarily Knowledge Bases (KBs).
    *   **`<mode-slug>/kb/`**: Each mode defined in `.roomodes` should have a corresponding directory here containing its knowledge base, typically starting with a `README.md`. The relevant Team Lead or primary mode (e.g., `lead-architect`, `product-owner`) is generally responsible for maintaining the content of their respective KB.
*   **`tasks/`**: Stores task files created via the manual saving workaround (see Global Rules). Files follow the `TASK-{Assignee}-{YYYYMMDDHHMMSS}.md` convention.
*   **`templates/`**: Contains standardized templates for various documents or artifacts (e.g., `adr_template.md`, `template-v1.md` for tasks).

## `.roomodes` File

This JSON file is the definitive source defining **all** custom modes (agents) available in the project, including specialized roles like `lead-architect`, `product-owner`, and utility modes like `agent-mcp-manager`. Each mode definition includes:

*   `slug`: A unique identifier for the mode.
*   `name`: A user-friendly name for the mode.
*   `roleDefinition`: A description of the mode's purpose and responsibilities.
*   `operationalGuidelines`: Specific instructions on how the mode should operate, often referencing its KB.
*   `groups`: Defines the permissions or capabilities assigned to the mode (e.g., file editing, command execution).

Refer to the specific files and directories mentioned above for more detailed information.