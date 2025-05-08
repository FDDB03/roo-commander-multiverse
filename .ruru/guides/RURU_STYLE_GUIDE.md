# .ruru Documentation Style Guide 🎨

This guide provides basic style and formatting conventions for documentation within the `.ruru` directory structure (including guides, KBs, templates, etc.).

## General Principles 📌

*   **Clarity:** Write clearly and concisely. Avoid ambiguity. Define acronyms on first use.
*   **Consistency:** Maintain consistent terminology, formatting, and structure across documents.
*   **Audience:** Consider the intended audience (usually other modes or developers) and tailor the language and detail level appropriately.
*   **Accuracy:** Ensure information is up-to-date and technically correct.

## Formatting 📝

*   **File Format:** Use Markdown (`.md`) for all documentation files.
*   **Headings:** Use `#` for headings. Start with `#` for the main title, `##` for major sections, `###` for subsections, etc. Leave a blank line before and after headings.
*   **Emphasis:** Use `**bold**` for strong emphasis or highlighting key terms/actions. Use `*italic*` for mild emphasis or titles.
*   **Code:**
    *   Use backticks `` `code` `` for inline code snippets, filenames, commands, or mode slugs.
    *   Use triple backticks with a language identifier for code blocks:
        ```markdown
        ```python
        def hello():
            print("Hello, world!")
        ```
*   **Lists:**
    *   Use `*` or `-` for unordered lists. Indent nested lists.
    *   Use `1.`, `2.`, etc., for ordered lists.
*   **Links:** Use standard Markdown link format: `[Link Text](URL or relative/path/to/file.md)`.
*   **Tables:** Use Markdown table syntax for structured data where appropriate.

## Content Conventions 📜

*   **Filenames:** Use lowercase letters, numbers, and hyphens (`-`) for filenames (e.g., `mode-selection-guide.md`).
*   **Placeholders:** In templates, use curly braces for placeholders: `{Placeholder Name}`.
*   **Mode References:** Refer to modes by their slug enclosed in backticks (e.g., `code`, `architect`).
*   **File Paths:** Enclose file paths in backticks (e.g., `.ruru/templates/adr_template.md`). Use relative paths from the project root where possible.

## 🎨 Emoji Usage

*   Use emojis thoughtfully to enhance readability and friendliness in user-facing documents (like KBs, guides, and interactive prompts).
*   Avoid overuse or emojis that might obscure meaning or look unprofessional in certain contexts.
*   Stick to commonly understood and generally positive or neutral emojis.
*   Ensure emojis render correctly across common platforms if possible.
*   Consider adding emojis to section headers, list items for emphasis, or to highlight calls to action or important notes.

## Review ✅

Ensure documentation is reviewed for clarity, accuracy, and adherence to these guidelines before finalizing.