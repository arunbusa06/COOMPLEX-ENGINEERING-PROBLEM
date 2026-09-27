# Todo App

A lightweight, responsive, client-side task management web application built with vanilla JavaScript, HTML5, and CSS3, styled with Bootstrap 5 and Font Awesome.

---

## Overview

The **Todo App** provides an intuitive interface for managing personal tasks directly within the web browser. The application runs entirely on the client side without requiring any backend server, database, or external build toolchain. Task data is stored locally in the browser's `localStorage`, allowing users to retain their task list across browser sessions.

A live deployment of the application is available at:
**[Live Demo on Netlify](https://todo-app-by-aklilu-mandefro.netlify.app/)**

---

## Preview

| Desktop View | Interaction Demo |
| :---: | :---: |
| ![Todo App Screenshot](https://i.imgur.com/lhWAtPR.png) | ![Todo App Interaction](https://i.imgur.com/3TlcB9q.gif) |

---

## Features

- **Task Creation Modal:** Add tasks with a title, due date, and detailed description via a clean Bootstrap modal dialog.
- **Input Validation:** Enforces mandatory fields (title, date, description) with inline feedback before task submission.
- **Automatic Date Sorting:** Tasks are automatically ordered chronologically by due date (`new Date(a.date) - new Date(b.date)`).
- **Persistent Storage:** Tasks are serialized as JSON and saved to the browser's `localStorage` for cross-session persistence.
- **Task Management Actions:**
  - **Edit Task:** Prefills the modal with the task details for in-place updates.
  - **Delete Task:** Immediately removes an individual task from the list and storage.
  - **Toggle Completion:** Visually strikes through completed tasks and lowers opacity using the checkmark action.
  - **Clear All:** Clears all stored tasks and resets the display in a single action.
- **Responsive Layout:** Centered, mobile-friendly card layout with custom scrollable task list.
- **Zero Dependencies Build:** Runs directly in any modern browser without npm, Node.js, or compilation steps.

---

## Technologies Used

| Technology | Purpose | Implementation Details |
| :--- | :--- | :--- |
| **HTML5** | Application structure & semantic markup | Modal dialogs, input controls, container elements |
| **CSS3** | Layout and visual styling | Flexbox, CSS Grid, custom scrollbar styling, card aesthetics |
| **JavaScript (ES6+)** | Application logic & DOM manipulation | Event listeners, `localStorage` API, array sorting, dynamic template strings |
| **Bootstrap 5.1.3** | Component styling & modal behavior | CDN-hosted responsive utility classes and modal JS bundle |
| **Font Awesome 5.15.4** | UI iconography | CDN-hosted icons for add (`fa-plus`), edit (`fa-edit`), delete (`fa-trash-alt`), and complete (`fa-check-circle`) |

---

## Project Structure

```text
todo-app-in-javascript-html-and-css/
│
├── index.html                   # Core HTML document and DOM layout
├── main.js                      # Application logic, state handling, and DOM operations
├── style.css                    # Custom CSS styling and responsive rules
├── README.md                    # Project overview, setup instructions, and reference
├── CONTRIBUTING.md              # Contributor guidelines, git workflow, and standards
│
├── docs/
│   ├── USER_GUIDE.md            # Detailed end-user guide and task management walkthrough
│   └── TROUBLESHOOTING.md       # Diagnostic solutions for common browser and runtime issues
│
└── .github/
    ├── ISSUE_TEMPLATE/
    │   ├── bug_report.md        # Structured template for submitting bug reports
    │   └── feature_request.md   # Structured template for proposing enhancements
    │
    └── PULL_REQUEST_TEMPLATE.md # Standard checklist for submitting pull requests
```

### Component Roles

- **`index.html`**: Defines the user interface, including the modal submission form, task list container, and external CDN dependencies (Bootstrap and Font Awesome).
- **`style.css`**: Defines card dimensions (300px × 500px), green theme palette (`#abcea1`), flex centering, and `.completed` state styling.
- **`main.js`**: Handles form submission, field validation, JSON serialization for `localStorage`, chronological task sorting, dynamic HTML generation, and task deletion/editing.

---

## Getting Started

### Prerequisites

To run this application, you only need:
- A modern web browser (Google Chrome, Mozilla Firefox, Microsoft Edge, Safari, or Brave).
- A local copy of this repository (via `git clone` or ZIP download).
- No Node.js, npm, Python, or web server is strictly required to run the core application.

### Installation / Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Aklilu-Mandefro/todo-app-in-javascript-html-and-css.git
   ```

2. **Navigate to the project directory:**
   ```bash
   cd todo-app-in-javascript-html-and-css
   ```

### Running the Application

Choose one of the following methods to launch the app:

#### Method 1: Direct File Opening (Simplest)
Open `index.html` directly in your default browser:
- **Windows:** Double-click `index.html` in File Explorer, or run:
  ```powershell
  Start-Process index.html
  ```
- **macOS:**
  ```bash
  open index.html
  ```
- **Linux:**
  ```bash
  xdg-open index.html
  ```

#### Method 2: Local HTTP Server (Recommended for Development)
Running a local development server ensures complete compatibility with browser security policies:

- **Using Python 3:**
  ```bash
  python -m http.server 8000
  ```
  Then navigate to `http://localhost:8000` in your browser.

- **Using VS Code Live Server:**
  If using Visual Studio Code, install the **Live Server** extension, right-click `index.html`, and select **Open with Live Server**.

- **Using Node.js (`npx serve` or `http-server`):**
  ```bash
  npx serve .
  ```

---

## How to Use

### Adding a Todo
1. Click the **Add New Task** bar (`+` icon) on the main card.
2. In the modal dialog, fill in:
   - **Task Title**: The name or subject of the task.
   - **Due Date**: The date by which the task should be completed (selected via the date picker).
   - **Description**: Detailed notes or instructions for the task.
3. Click the **Add** button.
   - *Note:* If any field is left empty, an error message ("All fields are required") appears in red, and the modal remains open.
4. Once valid data is entered, the modal automatically closes, and the new task is appended and sorted into the task list.

### Completing a Todo
- Click the green **Check Circle** icon (`fa-check-circle`) in the task's action row.
- The task item will toggle to a completed visual state (strikethrough text with reduced opacity).
- Clicking the icon again toggles the task back to the active state.

### Editing a Todo
- Click the blue/dark **Edit** icon (`fa-edit`) on any task card.
- The task form opens with the task's current title, due date, and description prefilled.
- Modify the fields as needed and click **Add** to save your changes.

### Removing a Todo
- **Individual Task:** Click the **Trash** icon (`fa-trash-alt`) on the task card. The task is immediately removed from the screen and deleted from browser storage.
- **Clear All Tasks:** Click the red **Clear All Tasks** button at the top of the card. This action purges all tasks from the list and clears the `localStorage` key.

For comprehensive operational instructions and screenshots, refer to the [User Guide](docs/USER_GUIDE.md).

---

## Application Workflow

The diagram below illustrates how user interactions flow through the application and interact with browser storage:

```text
+-------------------------------------------------------------------------+
|                              User Interface                             |
+-------------------------------------------------------------------------+
          |                                            |
   [Add New Task]                              [Clear All Tasks]
          |                                            |
  +---------------+                            +------------------+
  |  Open Modal   |                            | Clear Local Array|
  +---------------+                            | Remove from Store|
          |                                    | Re-render (Empty)|
    Enter Fields                               +------------------+
          |
    [Click Add]
          |
    +-----------+      Invalid
    | Validate? | -------------> Display "All fields are required"
    +-----------+
          | Valid
          v
  +-------------------------------------------------------+
  | 1. Append task object to `data` array                 |
  | 2. Serialize and save: localStorage.setItem('data')  |
  | 3. Sort tasks chronologically by due date            |
  | 4. Re-render task cards into DOM                      |
  | 5. Reset form inputs & close modal                   |
  +-------------------------------------------------------+
          |
          +-------------------------------+
          |                               |
    [Click Check]                   [Click Edit]
          |                               |
  Toggle .completed               Prefill form inputs
  (strikethrough / opacity)       Remove old entry & re-save
```

---

## Browser Compatibility

The application utilizes standard Web APIs (`localStorage`, ES6 Arrow Functions, `querySelector`/`getElementById`, `JSON.parse`/`JSON.stringify`) supported by all modern browsers:

| Browser | Supported Versions | Notes |
| :--- | :--- | :--- |
| **Google Chrome** | 60+ | Full support |
| **Mozilla Firefox** | 55+ | Full support |
| **Microsoft Edge** | 79+ (Chromium) | Full support |
| **Apple Safari** | 11+ | Full support |
| **Opera** | 47+ | Full support |

> [!NOTE]
> An active internet connection is required on initial load to fetch Bootstrap CSS/JS and Font Awesome from their respective CDNs. Once cached, the app operates offline.

---

## Troubleshooting

Common issues and quick solutions:

- **Tasks disappear after closing the browser:** Ensure your browser is not running in Incognito / Private Browsing mode, or configured to clear cookies and site data on exit.
- **Form does not submit:** Verify that all three fields (Title, Due Date, and Description) are filled out. All fields are mandatory.
- **Styling or icons missing:** Ensure your device has an active internet connection to load the Bootstrap and Font Awesome CDN assets.
- **Completed strikethrough resets on refresh:** In the current implementation, the completion toggle is a DOM-level state and is not stored in `localStorage`.

For in-depth explanations and diagnostic steps, see the complete [Troubleshooting Guide](docs/TROUBLESHOOTING.md).

---

## Contributing

Contributions are welcome and appreciated! Whether reporting bugs, suggesting enhancements, or submitting documentation updates, please read our contributor documentation before getting started:

- [Contributor Guide](CONTRIBUTING.md) — Step-by-step instructions on branch naming, coding style, testing, and pull requests.
- [Bug Report Template](.github/ISSUE_TEMPLATE/bug_report.md) — For submitting reproducible defect reports.
- [Feature Request Template](.github/ISSUE_TEMPLATE/feature_request.md) — For proposing new features and improvements.
- [Pull Request Template](.github/PULL_REQUEST_TEMPLATE.md) — Standard checklist for pull request submissions.

### Quick Contribution Steps

1. Fork the repository on GitHub.
2. Create a topic branch:
   ```bash
   git checkout -b docs/improve-setup-instructions
   ```
3. Test your changes locally in a web browser.
4. Commit your changes using descriptive commit messages:
   ```bash
   git commit -m "docs: improve setup instructions for local development"
   ```
5. Push to your fork:
   ```bash
   git push origin docs/improve-setup-instructions
   ```
6. Open a Pull Request referencing the relevant issue.

---

## Issue Reporting

If you encounter any problems or have ideas for enhancement, please open an issue on GitHub:
- [Submit a Bug Report](https://github.com/Aklilu-Mandefro/todo-app-in-javascript-html-and-css/issues) using the [Bug Report Template](.github/ISSUE_TEMPLATE/bug_report.md).
- [Submit a Feature Request](https://github.com/Aklilu-Mandefro/todo-app-in-javascript-html-and-css/issues) using the [Feature Request Template](.github/ISSUE_TEMPLATE/feature_request.md).

---

## Pull Requests

When submitting a pull request:
1. Ensure your branch is up to date with `main`.
2. Verify that existing features continue to work as expected.
3. Fill out the [Pull Request Template](.github/PULL_REQUEST_TEMPLATE.md) completely with details of what was changed and how it was tested.

---

## License

This project currently does not include an explicit open-source license file in the repository root. All rights reside with the original author, [Aklilu Mandefro](https://github.com/Aklilu-Mandefro). Contributors are encouraged to consult with the repository maintainer regarding open-source licensing (such as the MIT License) for future releases.

---

## Acknowledgements

- Original Author: [Aklilu Mandefro](https://github.com/Aklilu-Mandefro)
- UI Icons: [Font Awesome](https://fontawesome.com/)
- UI Framework: [Bootstrap 5](https://getbootstrap.com/)
- Hosting: [Netlify](https://www.netlify.com/)
