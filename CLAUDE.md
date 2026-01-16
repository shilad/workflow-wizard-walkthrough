# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an interactive HTML/JavaScript-based workflow wizard for student onboarding and environment setup (specifically for Comp 127 at Macalester College). It guides students through step-by-step installation and configuration of their development environment using a browser-based wizard interface.

## Commands

```bash
# Format code (HTML, JS, CSS, JSON)
make prettier

# Check formatting without modifying
make check-prettier

# Run locally
python -m http.server 8000
```

Deployment is via GitHub Pages.

## Architecture

**Configuration-driven single-page application:**

- **workflow_config.json** - Defines the entire workflow as nested JSON (steps, titles, content files, navigation actions)
- **workflow.js** - `WorkflowManager` class handles state management, step navigation, platform detection, browser history integration, and dynamic content loading
- **index.html** - Single-page app shell with placeholder containers
- **styles.css** - Visual presentation with CSS variables
- **\*.html files** (step-welcome.html, install-java.html, etc.) - Content fragments loaded dynamically based on current step

**Key design patterns:**
- URL-based navigation (`?step=stepName`) for deep linking and browser back/forward support
- Platform-aware content using localStorage to remember macOS/Windows/Linux selection
- Content fragments are injected into the main page rather than full page reloads

**To create a new workflow:** Use `workflow_template.json` as a reference for the JSON structure.

## Important Notes

- No npm/package.json - this is vanilla JavaScript with no framework dependencies
- Images for step instructions are stored in `images/` directory
- `instructor_notes.md` contains field-tested troubleshooting tips for common student issues
