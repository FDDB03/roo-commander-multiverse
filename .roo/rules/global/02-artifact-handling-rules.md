# Global Rules: Artifact Handling

This file contains global rules and guidelines related to the creation, usage, and naming of templates and artifacts.

## Template and Artifact Usage Guideline

**Guideline:** When creating standard documents like Architecture Decision Records (ADRs), Test Plans, Implementation Plans, User Stories, etc.:
1.  Check the `.ruru/templates/` directory for a relevant template file (e.g., `adr_template.md`, `test_plan_template.md`).
2.  If a suitable template exists, use it as the basis for the new document.
3.  Save the completed document (artifact) in the `.ruru/artifacts/` directory, potentially within a subdirectory relevant to the document type or project (e.g., `.ruru/artifacts/adrs/`, `.ruru/artifacts/plans/`, `.ruru/artifacts/project-x/test-plans/`). Use clear, descriptive filenames.

**Rationale:** Promotes consistency in documentation, leverages predefined structures, and provides a central location for important project artifacts.

## Artifact Naming Convention Guideline

**Guideline:** When saving artifacts (documents created from templates) to the `.ruru/artifacts/` directory, use a consistent naming convention:
`{DocumentType}-{Identifier}.{ext}`
*   `{DocumentType}`: A short code indicating the type (e.g., `ADR`, `Plan`, `TestPlan`, `UserStory`, `BugReport`, `StyleGuide`, `API`).
*   `{Identifier}`: A brief, descriptive identifier, often using hyphens for spaces (e.g., `Auth-Service-Refactor`, `Login-Flow`, `User-Profile-API`). Avoid overly long names.
*   `{ext}`: The file extension (usually `.md`).

**Examples:**
*   `ADR-Auth-Service-Refactor.md`
*   `TestPlan-Payment-Gateway-Integration.md`
*   `UserStory-Create-User-Profile.md`
*   `BugReport-Login-Button-Disabled.md`

**Rationale:** Ensures predictable and easily searchable filenames for project artifacts.