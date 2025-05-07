# Contributing Rules and Templates

This guide outlines the process for adding or modifying mode-specific rules (`.roo/rules-<mode-slug>/`) and document templates (`.ruru/templates/`).

## Contributing Rules

*   **Purpose:** Rules define specific behaviors, constraints, or automated checks for modes.
*   **Location:** Mode-specific rules go in the corresponding `.roo/rules-<mode-slug>/` directory. Global rules are in `.roo/rules/global-rules.md`.
*   **Naming Convention:** Follow the `NN-<short-description>-rule.md` format (see `global-rules.md` for details).
*   **Content:** Rules should be clearly written in Markdown, explaining the rule's logic, rationale, and any potential impact.
*   **Process:**
    1.  Discuss the proposed rule with the relevant team or lead (e.g., Lead Architect, Head of Development).
    2.  Create or modify the rule file in the appropriate directory.
    3.  Test the rule's effect if possible.
    4.  Submit the change for review (e.g., via pull request if using version control).

## Contributing Templates

*   **Purpose:** Templates provide standardized structures for common documents and artifacts.
*   **Location:** All templates reside in `.ruru/templates/`.
*   **Naming Convention:** Use descriptive names like `type_template.md` (e.g., `adr_template.md`, `test_plan_template.md`).
*   **Content:** Templates should use Markdown and include clear placeholders (e.g., `{Placeholder Name}`) and comments where necessary to guide usage. Reference the task template (`template-v1.md`) for examples.
*   **Process:**
    1.  Identify the need for a new template or modification.
    2.  Discuss with the relevant lead (e.g., Technical Writing Lead, QA Lead).
    3.  Create or modify the template file in `.ruru/templates/`.
    4.  Update any relevant guidelines (e.g., `global-rules.md`) to reference the new/modified template if necessary.
    5.  Submit the change for review.

*Self-Correction: Added placeholder content for the new guide.*