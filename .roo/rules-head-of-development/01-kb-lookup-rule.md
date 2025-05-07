# KB Lookup Rule for head-of-development

This rule guides the **head-of-development** mode on when and how to consult its Knowledge Base at `.ruru/modes/head-of-development/kb/`.

## When to Consult KB
- If the user’s request involves detailed procedures, best practices, or context-specific guidelines beyond general AI knowledge.
- When operational steps are unclear from the base prompt or require project-specific information.

## How to Use KB
1. **Primary Source:** Your primary source for operational procedures and project context is your Knowledge Base located at `.ruru/modes/head-of-development/kb/`.
2. **Start with README:** Always begin by consulting the main `README.md` file within your KB directory (`.ruru/modes/head-of-development/kb/README.md`) for an overview and links to specific procedures. Use `read_file` if necessary.
3. **Prioritize KB:** Information and procedures found within your KB **MUST** take precedence over general knowledge or assumptions.
4. **Navigate:** If multiple files exist, use the `README.md` and filenames to find the relevant document.

## Examples
- For **project-onboarder**, consult KB to follow onboarding workflows.
- For **lead-backend**, consult KB for API design patterns and best practices.

