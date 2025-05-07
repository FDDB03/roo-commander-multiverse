# Project Journaling Guide

This guide provides best practices for using the project journal located at `.ruru/journal/journal.md`.

## Purpose

The project journal serves as a chronological log of significant events, decisions, outcomes, and context shifts during the project lifecycle. It aids in:

*   **Traceability:** Understanding why certain decisions were made.
*   **Context Sharing:** Providing background for team members or modes joining later.
*   **Knowledge Retention:** Capturing key learnings and resolutions.
*   **Auditing:** Reviewing the sequence of events if needed.

## When to Add Entries

Modes should consider adding journal entries for:

*   Completion of major tasks, features, or milestones.
*   Key architectural or strategic decisions made (link to ADRs if applicable).
*   Significant technical challenges encountered and their resolutions.
*   Persistent or impactful errors and how they were addressed.
*   Important user feedback received that influences direction.
*   Mode switches where significant context needs to be preserved or transferred.
*   Adoption of new tools, libraries, or significant changes to the tech stack.
*   Security incidents or significant vulnerability findings/fixes.
*   Major changes to project scope or requirements.

## Format

Use the established header format for each entry, as defined in `global-rules.md`:

```markdown
## YYYY-MM-DD HH:MM - {Author/Mode} - {Summary}

{Detailed description of the event, decision, or outcome. Be concise but clear. Use bullet points for lists. Link to relevant artifacts, tasks, or code if possible.}
```

*   **Timestamp:** Use the current date and time (YYYY-MM-DD HH:MM).
*   **Author/Mode:** Indicate which mode or person is making the entry (e.g., `code`, `architect`, `qa-lead`).
*   **Summary:** A brief, descriptive title for the entry.
*   **Details:** Provide sufficient detail for someone else to understand the context and significance of the entry.

## Best Practices

*   **Be Timely:** Add entries as soon as possible after the event occurs.
*   **Be Objective:** Stick to the facts of the event or decision.
*   **Be Clear and Concise:** Avoid jargon where possible; explain necessary technical terms briefly.
*   **Link Relevant Information:** Reference related tasks, artifacts (ADRs, plans), code commits, or external documentation.
*   **Review Periodically:** Occasionally review recent journal entries to ensure important context isn't being missed.