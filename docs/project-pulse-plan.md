# Project Pulse implementation plan

## Summary

Build Mona's Project Pulse dashboard as a lightweight, polished static web app that renders project status cards from structured JSON data. The work should be split between design and implementation responsibilities, with the Orchestrator coordinating sequencing and verification. The result should be easy to preview in a Codespace and clearly reflect a project health dashboard rather than a generic page.

## Ordered implementation steps

1. Define the dashboard structure and data contract
   - Confirm the page layout: header, summary strip, project cards, status badges, and a responsive dashboard container.
   - Define the project data shape in `app/project-data.json` so the UI can render name, owner, status, priority, health score, deadline, and owner notes.
   - Decide how empty states, loading states, and invalid data should be handled if the JSON is incomplete.

2. Create the design direction and visual system
   - Designer defines the information hierarchy, spacing, color treatments, card layout, badges, and typography.
   - Designer sets the CSS hooks and class names so the app matches a realistic dashboard aesthetic (`.dashboard`, `.project-card`, `.status-badge`, etc.).
   - Designer reviews the logical flow to ensure the dashboard immediately communicates project health and priority.

3. Implement the HTML shell
   - Coder creates `app/index.html` with the dashboard container, sections for portfolio summary, and a card template or repeated project list.
   - The page should mount the data from `app/project-data.json` and render the semantic structure needed for a clean dashboard.
   - Keep the HTML accessible, with readable headings, logical ordering, and strong contrast.

4. Build the styling layer
   - Designer owns the final look and feel in `app/styles.css`.
   - Coder implements the CSS structure and responsive behavior so cards stack gracefully on smaller screens.
   - Ensure consistent spacing, borders, shadows, and status styling across all project cards.

5. Add the project data source
   - Coder creates `app/project-data.json` containing realistic project entries with statuses, priorities, owners, and health signals.
   - Coder keeps the file deterministic and easy to edit for future iterations.
   - Designer checks whether the data categories and labels support the intended dashboard narrative.

6. Add launch support for Codespace preview
   - Coder creates `.vscode/launch.json` so the app can be opened directly in the browser from the workspace.
   - Configure the launch target to open `index.html` from the `app` folder and use a predictable local preview path.

7. Validate the integrated dashboard
   - Confirm the HTML renders correctly, CSS applies the intended dashboard look, and data loads in the expected structure.
   - Check the page in a browser or preview mode and verify responsive behavior and legibility.

## File assignments

- `app/index.html` — Coder primary owner; Designer reviews layout and UX clarity.
- `app/styles.css` — Designer primary owner; Coder implements the final CSS structure and responsive rules.
- `app/project-data.json` — Coder primary owner; Designer validates that the data model supports the dashboard experience.
- `.vscode/launch.json` — Coder primary owner; Orchestrator ensures it matches the app preview requirements.

## Designer responsibilities

- Define the dashboard information architecture and visual hierarchy.
- Create a polished, readable project pulse aesthetic with strong status differentiation.
- Establish consistent UI patterns for cards, badges, spacing, typography, and responsiveness.
- Review whether the page clearly communicates project health and priorities to a user at a glance.

## Coder responsibilities

- Implement the HTML structure and data binding logic for the dashboard.
- Add or update the JSON dataset and keep the front-end data contract consistent.
- Build the CSS implementation to match the approved design direction.
- Create the local preview support in `.vscode/launch.json` for the Codespace environment.
- Validate that the dashboard works end-to-end and remains easy to maintain.

## Dependencies

- The dashboard markup depends on the data schema defined in `app/project-data.json`.
- The CSS depends on the final HTML structure and class names used in `app/index.html`.
- The preview configuration in `.vscode/launch.json` depends on the app folder layout and final file names.
- Design approval should precede final styling refinements, but the basic structure can be created in parallel with the data model.

## Parallel work decisions

- Parallel work can proceed in the first phase:
  - Designer can draft the dashboard design system and card treatment while Coder defines the JSON schema.
  - Coder can begin scaffolding `app/index.html` and the data file while the visual direction is still being refined.
- Sequential work should be enforced for final polish:
  - Final `app/styles.css` should be adjusted after the HTML structure is stable.
  - Preview configuration should be added after the app file layout is finalized.
  - Final validation should occur only after all files are integrated.

## Validation expectations

- HTML loads without broken structure and contains clear sections for project overview and project cards.
- CSS creates a consistent dashboard look with strong contrast, readable type, badge hierarchy, and responsive behavior.
- JSON data is valid and matches the expected fields used by the front-end.
- The app can be launched from the Codespace and opens the dashboard directly instead of a directory listing.
- The final page reads like a polished Project Pulse dashboard, not a generic placeholder layout.

## Open questions

- Should the project cards be static only, or should there be lightweight interactivity such as filtering by status or priority?
- Should the dashboard include a top summary row for metrics like active projects, at-risk items, and completion rate?
- Does Mona want a single default dataset or a more realistic multi-team view with grouped project categories?
