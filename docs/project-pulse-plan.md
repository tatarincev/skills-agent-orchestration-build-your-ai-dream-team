# Project Pulse implementation plan

## Goal

Build a lightweight, polished static dashboard that helps Mona's contributors quickly see active projects, owners, status, recent activity, priority or risk, and a short contributor-friendly summary. The page must render project cards from JSON data and be easy to preview through the **Run Project Pulse Dashboard** VS Code launch configuration.

## Responsibilities and file assignments

| Owner | Responsibility | Assigned files |
|---|---|---|
| Orchestrator | Coordinate the phases, preserve clear file ownership, sequence dependent work, integrate the result, and confirm the final validation. | No implementation files; review all deliverables. |
| Planner | Define this plan, its dependencies, parallel work, and validation expectations. | `docs/project-pulse-plan.md` |
| Designer | Specify the visual hierarchy, card layout, status and priority treatment, accessible markup expectations, readable spacing, and responsive behavior. Provide implementation guidance without editing Coder-owned files. | Design guidance for `app/index.html` and `app/styles.css`; no file edits. |
| Coder | Implement the static dashboard and its runnable preview, following the brief and Designer's guidance. | `app/index.html`, `app/styles.css`, `app/project-data.json`, `.vscode/launch.json` |

## Phases

1. **Set design direction — Designer.** Define a clear dashboard first view, project-card information order, status badges and priority emphasis, readable typography and spacing, keyboard/accessibility expectations, responsive layout, and deterministic `.dashboard` and `.project-card` hooks. Return concise guidance for the Coder.
2. **Prepare independent artifacts — Coder.** Create `app/project-data.json` with a top-level `projects` array and entries containing `name`, `owner`, `status`, `recentActivity`, and `priority`. Create `.vscode/launch.json` as strict JSON with a **Run Project Pulse Dashboard** configuration that serves from `${workspaceFolder}/app` using `python3 -m http.server 5500` and opens `http://localhost:%s/index.html`, not the directory root.
3. **Build the dashboard page and styling — Coder.** After receiving Designer's guidance and confirming the data shape, implement `app/index.html` and `app/styles.css`. Use the exact title **Project Pulse**, reference the stylesheet and JSON data, render visible `.project-card` elements from the projects data, and show each project's required fields. Use accessible semantic structure and responsive, polished card styling.
4. **Integrate and validate — Orchestrator with Coder.** Check that the files agree on selectors, data fields, and paths. Run the validation checks below and report any remaining limitations.

## Dependencies and parallel work

- The Designer's guidance is a prerequisite for the Coder's final page layout and styles. Keep Designer's role advisory so there is no competing edit scope.
- The data file and launch configuration can be prepared in parallel with the Designer's design guidance: their required schema and preview behavior are defined in the brief and do not depend on visual decisions.
- The HTML and CSS implementation follows both the design guidance and the data schema. The Coder should coordinate these as one page-and-style implementation to keep markup hooks and styles consistent.
- Integration and final validation happen after all four assigned deliverables exist.
- Do not parallelize edits to the same file; the Coder owns all four implementation files.

## Validation expectations

- Confirm all assigned files exist and `app/project-data.json` and `.vscode/launch.json` parse as JSON.
- Confirm `app/index.html` has the exact **Project Pulse** title, references `styles.css` and `project-data.json`, and renders project cards with the `project-card` class.
- Confirm each data record has `name`, `owner`, `status`, `recentActivity`, and `priority`, and the page visibly presents the required project information.
- Confirm `app/styles.css` defines `.dashboard` and `.project-card`, includes rounded corners and shadows, and provides a responsive layout with readable contrast and spacing.
- Confirm the launch configuration is named **Run Project Pulse Dashboard**, runs `python3 -m http.server 5500` from `${workspaceFolder}/app`, and opens `index.html` at `http://localhost:%s/index.html`.
- Run **Run Project Pulse Dashboard** and verify the browser displays the dashboard UI rather than a directory listing. Stop the preview server after the check.
