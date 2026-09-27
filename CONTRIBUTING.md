# Contributing Guidelines

Thank you for your interest in contributing to the **Todo App** project! We welcome contributions of all kinds, including bug fixes, feature enhancements, documentation improvements, and feedback.

This document outlines the workflow, guidelines, and standards for contributing effectively to this repository.

---

## Table of Contents

- [Before You Start](#before-you-start)
- [Documentation Workflow](#documentation-workflow)
- [Forking the Repository](#forking-the-repository)
- [Creating a Branch](#creating-a-branch)
- [Making Changes](#making-changes)
- [Testing Your Changes](#testing-your-changes)
- [Commit Message Guidelines](#commit-message-guidelines)
- [Pull Request Guidelines](#pull-request-guidelines)
- [Issue Reporting](#issue-reporting)
- [Documentation Contributions](#documentation-contributions)
- [Code of Conduct and Community Expectations](#code-of-conduct-and-community-expectations)

---

## Before You Start

Before starting any work:
1. **Search existing issues and pull requests** to check if the topic or defect is already being addressed.
2. **Open an issue first** if you are proposing a substantial feature or architectural change, so maintainers and contributors can discuss the approach.
3. For small fixes, typos, or documentation clarifications, you may proceed directly with a pull request.

---

## Documentation Workflow

All contributions follow a standard Git and GitHub workflow:

```text
Fork Repository
      │
      ▼
Clone to Local Machine
      │
      ▼
Create Dedicated Branch (docs/*, fix/*, feature/*)
      │
      ▼
Make Changes & Verify Code/Docs
      │
      ▼
Test in Web Browser / Check Links
      │
      ▼
Commit with Descriptive Message
      │
      ▼
Push to Your Fork
      │
      ▼
Open Pull Request on GitHub
      │
      ▼
Peer Review & Discussion
      │
      ▼
Merge into Main Branch
```

### Purpose of Each Stage

| Stage | Purpose |
| :--- | :--- |
| **Fork** | Creates an isolated copy of the repository under your personal GitHub account where you have write access. |
| **Clone** | Downloads your fork onto your local workstation for development. |
| **Branch** | Keeps changes isolated from the default branch, preventing conflicts and keeping PRs focused. |
| **Make Changes** | Implementation of code or documentation updates according to project guidelines. |
| **Test / Review** | Local verification in multiple browsers, checking console logs, and validating Markdown links. |
| **Commit** | Records clear, atomic snapshots of work with explanatory messages. |
| **Push** | Uploads the committed branch from your local workstation to your remote fork on GitHub. |
| **Pull Request** | Formally requests review and integration into the upstream repository using the PR template. |
| **Review** | Maintainers review code quality, documentation accuracy, and test results before approval. |
| **Merge** | The final step where approved changes are incorporated into the upstream `main` branch. |

---

## Forking the Repository

1. Navigate to the upstream repository:  
   `https://github.com/Aklilu-Mandefro/todo-app-in-javascript-html-and-css`
2. Click the **Fork** button in the upper-right corner of the page.
3. Select your GitHub account as the destination.
4. Clone your personal fork locally:
   ```bash
   git clone https://github.com/<your-username>/todo-app-in-javascript-html-and-css.git
   cd todo-app-in-javascript-html-and-css
   ```
5. Configure the upstream remote to stay in sync with the primary repository:
   ```bash
   git remote add upstream https://github.com/Aklilu-Mandefro/todo-app-in-javascript-html-and-css.git
   git fetch upstream
   ```

---

## Creating a Branch

Always create a dedicated feature or documentation branch before editing files. Do not commit directly to the `main` branch.

### Branch Naming Conventions

Use lowercase names with hyphens, prefixed by the change type:

| Prefix | Usage | Example |
| :--- | :--- | :--- |
| `docs/` | Documentation improvements, guides, typos | `docs/troubleshooting-guide-expansion` |
| `fix/` | Bug fixes and runtime corrections | `fix/form-validation-empty-check` |
| `feature/` | New functionality or UI enhancements | `feature/task-priority-labels` |
| `refactor/` | Code refactoring without changing functionality | `refactor/modularize-event-listeners` |
| `style/` | CSS layout adjustments and theme fixes | `style/fix-mobile-modal-spacing` |

Create and switch to your branch:
```bash
git checkout -b docs/improve-contributing-guide
```

---

## Making Changes

When modifying code or documentation:
- **Preserve existing functionality:** Do not rewrite or replace working application code unless fixing an identified bug.
- **Maintain simplicity:** This is a zero-dependency vanilla JS application. Do not introduce heavy build tools (Webpack, Vite), frameworks (React, Vue), or package managers (npm) unless specifically requested and approved.
- **Code style:**
  - Use clean, standard JavaScript (ES6+).
  - Use 2-space indentation.
  - Keep variable and function names self-descriptive (`formValidation`, `acceptData`, `createTasks`).
  - Keep CSS organized by component and layout.

---

## Testing Your Changes

Because this project does not use a test runner, verification is done directly in the browser:

1. **Open the Application:**
   - Open `index.html` directly in your browser or run a local web server:
     ```bash
     python -m http.server 8000
     ```
2. **Execute the Standard User Flow:**
   - Add a task with Title, Due Date, and Description.
   - Verify that incomplete submissions trigger the validation error message ("All fields are required").
   - Confirm that tasks sort chronologically by date.
   - Toggle completion using the checkmark icon and check the strike-through styling.
   - Edit an existing task, modify its fields, and confirm the changes save.
   - Delete an individual task using the trash icon.
   - Click "Clear All Tasks" and confirm all tasks are removed from the screen and storage.
3. **Inspect the Browser Console:**
   - Press `F12` (or `Ctrl+Shift+I` / `Cmd+Option+I`) to open Developer Tools.
   - Check the **Console** tab for any JavaScript exceptions or unhandled errors.
   - Inspect the **Application** (or **Storage**) tab -> **Local Storage** -> check that `data` updates correctly.
4. **Cross-Browser Verification:**
   - Test in at least two modern browsers (e.g., Google Chrome and Mozilla Firefox).

---

## Commit Message Guidelines

We follow the [Conventional Commits](https://www.conventionalcommits.org/) convention to keep git history readable, informative, and searchable.

### Format

```text
<type>: <short summary in imperative mood>

[optional detailed body explaining context and motivation]
```

### Commit Types

- `docs:` Changes exclusively to documentation files (README, USER_GUIDE, CONTRIBUTING, etc.)
- `fix:` A bug fix in HTML, CSS, or JavaScript
- `feat:` A new feature or user-facing improvement
- `style:` Changes that do not affect code logic (whitespace, CSS formatting)
- `refactor:` Code changes that neither fix a bug nor add a feature
- `chore:` Maintenance tasks, repository configuration, issue templates

### Good Examples

```text
docs: improve README structure and setup guide
docs: add troubleshooting guide for browser storage
fix: prevent empty date selection during task submission
feat: add confirmation dialog before clearing all tasks
```

### Poor Examples

```text
Update stuff
Fixed bug
changes
wip
```

---

## Pull Request Guidelines

When your changes are ready for review:

1. **Rebase or merge latest upstream changes:**
   ```bash
   git fetch upstream
   git merge upstream/main
   ```
2. **Push your branch to your fork:**
   ```bash
   git push -u origin docs/improve-contributing-guide
   ```
3. **Open the Pull Request:**
   - Go to your fork on GitHub and click **Compare & pull request**.
   - Ensure the base repository is `Aklilu-Mandefro/todo-app-in-javascript-html-and-css` and the base branch is `main`.
   - Provide a clear, descriptive title.
   - Complete every section of the [Pull Request Template](.github/PULL_REQUEST_TEMPLATE.md).
4. **Respond to feedback:**
   - Be receptive to feedback and comments from reviewers.
   - Push additional commits to your branch if updates are requested; the PR updates automatically.

---

## Issue Reporting

If you find a defect or have a feature idea:
- For bugs, use the [.github/ISSUE_TEMPLATE/bug_report.md](.github/ISSUE_TEMPLATE/bug_report.md) template and include exact steps to reproduce, browser version, and console logs.
- For features, use the [.github/ISSUE_TEMPLATE/feature_request.md](.github/ISSUE_TEMPLATE/feature_request.md) template and describe the use case, suggested solution, and benefits.

---

## Documentation Contributions

Documentation improvements are always welcome! When editing documentation:
- Verify that every code snippet or terminal command is accurate and tested.
- Check all relative links (e.g., `docs/USER_GUIDE.md`) to make sure they resolve properly.
- Ensure all markdown formatting is valid and readable in plain text.
- Do not introduce placeholder text, broken links, or unsupported claims.

---

## Code of Conduct and Community Expectations

To foster an inclusive, respectful, and productive community, all contributors and maintainers are expected to:
- Be polite, considerate, and professional in all communications (issues, PR reviews, comments).
- Respect differing perspectives and experiences.
- Offer and accept constructive feedback gracefully.
- Focus on what is best for the project and its users.
