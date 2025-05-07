# Git Workflow Guide

This guide outlines the standard Git workflow and commit message conventions to be used by modes interacting with version-controlled code or configuration.

## Basic Feature Branch Workflow

When making changes related to a specific task:

1.  **Ensure Local Repository is Up-to-Date:**
    *   Before starting work, switch to the main branch (e.g., `main` or `master`).
    *   Pull the latest changes: `git pull origin main` (replace `main` if needed).
2.  **Create a Feature Branch:**
    *   Create a new branch named descriptively, often including the task type and ID (if available). Convention: `type/task-id-short-description` (e.g., `feat/TASK-123-add-login-button`, `fix/TASK-456-null-pointer`).
    *   Command: `git checkout -b type/task-id-short-description`
3.  **Make Changes:** Implement the required code or configuration changes.
4.  **Stage Changes:** Add the modified files to the staging area.
    *   Command (add specific files): `git add path/to/file1 path/to/file2`
    *   Command (add all changes): `git add .` (Use with caution)
5.  **Commit Changes:** Commit the staged changes using the Conventional Commits format (see below).
    *   Command: `git commit -m "type(scope): subject"`
6.  **Push Branch:** Push the new branch and its commits to the remote repository.
    *   Command: `git push -u origin type/task-id-short-description`
7.  **Create Pull/Merge Request (If Applicable):** If the project uses PRs/MRs, this step would typically follow, often handled manually or via platform integrations outside this simulation's direct control unless specific rules/tools are added.

## Commit Message Convention (Conventional Commits)

All commit messages **MUST** follow the Conventional Commits specification (https://www.conventionalcommits.org/). The basic format is:

```
type(scope): subject

[optional body]

[optional footer(s)]
```

*   **`type`**: Describes the kind of change:
    *   `feat`: A new feature
    *   `fix`: A bug fix
    *   `build`: Changes affecting the build system or external dependencies
    *   `chore`: Other changes that don't modify src or test files
    *   `ci`: Changes to CI configuration files and scripts
    *   `docs`: Documentation only changes
    *   `perf`: A code change that improves performance
    *   `refactor`: A code change that neither fixes a bug nor adds a feature
    *   `revert`: Reverts a previous commit
    *   `style`: Changes that do not affect the meaning of the code (white-space, formatting, etc)
    *   `test`: Adding missing tests or correcting existing tests
*   **`scope` (optional)**: A noun describing the section of the codebase affected (e.g., `auth`, `ui`, `api`, `parser`).
*   **`subject`**: A short, imperative description of the change (e.g., `add login button`, `correct calculation error`). Use lowercase. Do not end with a period.
*   **`body` (optional)**: Provides additional context, motivation, or details about the change.
*   **`footer(s)` (optional)**: Used for referencing issues (e.g., `Fixes #123`) or noting breaking changes (`BREAKING CHANGE:`).

**Example Commit Message:**

```
feat(auth): implement password reset endpoint

Adds the POST /api/auth/reset-password endpoint.
Requires user email in the request body. Sends a reset token via email (email sending mocked for now).

Fixes #42
```

**Rationale:** Standardized workflows and commit messages improve collaboration, enable automated changelog generation, and make repository history easier to understand.