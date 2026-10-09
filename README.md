# hermes-agent-lesson

A single-file Todo List web app, deployed to GitHub Pages via GitHub Actions.

## Live site

https://emilyleung00.github.io/hermes-agent-lesson/

## What's in here

| Path | Purpose |
|---|---|
| `public/index.html` | The app — one self-contained HTML file |
| `.github/workflows/deploy-pages.yml` | Builds and deploys `public/` to GitHub Pages on every push to `main` |

## The app

A Todo List with no build step and no dependencies. Open `public/index.html` in a browser — no server required.

**Features**

- Add a task (Enter or the button); input is trimmed, whitespace collapsed, capped at 200 characters, blanks rejected
- Mark done / not done by clicking the checkbox or the label text
- Delete a single task, or clear all completed tasks at once
- Persists to `localStorage` — tasks *and* the active filter survive a reload
- Filter by all / active / completed, with a live counter
- Syncs live across browser tabs

**Design & accessibility**

- Follows the system light/dark preference via `prefers-color-scheme`
- Design tokens as CSS custom properties; keyboard operable; labelled controls for screen readers
- Honours `prefers-reduced-motion`
- Responsive down to 390px with no horizontal scroll
- Text and control contrast measured against WCAG AA (all ≥ 4.5:1; interactive controls ≥ 3:1)

**Safety**

- User input is rendered with `textContent`, never `innerHTML` — markup in a task is displayed as text, not executed
- Corrupt or unreadable `localStorage` data is repaired or discarded on load instead of breaking the page

## Deploying

Pushing to `main` triggers the workflow, which uploads `public/` as a Pages artifact and deploys it.

The repository's Pages source must be set to **GitHub Actions** (Settings → Pages → Build and deployment → Source). To publish a different folder, change `path` in the upload step of the workflow.
