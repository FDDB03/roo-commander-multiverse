# Code Review Checklist: {Project/Feature/PR Title}

*   **Author:** {Author Name}
*   **Reviewer(s):** {Reviewer Names}
*   **Date:** {YYYY-MM-DD}
*   **Pull Request Link:** {URL to PR}

---

## General Checks

*   [ ] **Functionality:** Does the code achieve its stated purpose according to the requirements/user story?
*   [ ] **Clarity/Readability:** Is the code easy to understand? Are variable/function names meaningful? Is the logic straightforward?
*   [ ] **Simplicity:** Is the code overly complex? Can it be simplified without sacrificing functionality? (KISS/YAGNI principles)
*   [ ] **Consistency:** Does the code adhere to the project's established coding standards and style guide?
*   [ ] **No Debug/Commented-Out Code:** Is there any leftover debugging code (e.g., `console.log`) or large blocks of commented-out code that should be removed?
*   [ ] **Error Handling:** Are potential errors handled gracefully? Are error messages informative?
*   [ ] **Resource Management:** Are resources (files, connections, memory) properly managed and released?

## Design & Architecture

*   [ ] **Adherence to Architecture:** Does the code align with the overall system architecture and design patterns?
*   [ ] **Modularity/Coupling:** Is the code well-structured into modules/components? Is coupling minimized?
*   [ ] **Single Responsibility Principle (SRP):** Do functions/classes have a single, well-defined responsibility?
*   [ ] **Duplication (DRY):** Is there significant code duplication that could be refactored into reusable functions/components?

## Testing

*   [ ] **Unit Tests:** Are there sufficient unit tests covering the new/changed logic? Do they pass?
*   [ ] **Integration Tests:** Are integration tests necessary and present/updated? Do they pass?
*   [ ] **Test Quality:** Are the tests well-written, readable, and testing the right things? Do they cover edge cases?
*   [ ] **Test Coverage:** Does the code meet the project's test coverage requirements?

## Performance

*   [ ] **Efficiency:** Are there any obvious performance bottlenecks (e.g., inefficient loops, unnecessary database queries)?
*   [ ] **Resource Usage:** Does the code seem efficient in terms of memory or CPU usage? (May require profiling for complex cases)

## Security (Consult Security Lead if unsure)

*   [ ] **Input Validation:** Is all external input properly validated/sanitized?
*   [ ] **Output Encoding:** Is output correctly encoded to prevent injection attacks (e.g., XSS)?
*   [ ] **Authentication/Authorization:** Are permissions checked correctly before performing actions or accessing data?
*   [ ] **Secrets Management:** Are secrets (API keys, passwords) handled securely and not hardcoded?
*   [ ] **Dependency Security:** Are third-party libraries up-to-date and free from known critical vulnerabilities? (SCA)
*   [ ] **Logging:** Is sensitive information avoided in logs?

## Documentation

*   [ ] **Code Comments:** Are complex or non-obvious parts of the code adequately commented?
*   [ ] **README/Docs Update:** Does project documentation (README, API docs, user guides) need to be updated to reflect these changes?

## Reviewer Comments Summary

{Provide a high-level summary of findings or key discussion points.}

---

**Approval Status:** {Approved | Approved with Comments | Changes Requested}