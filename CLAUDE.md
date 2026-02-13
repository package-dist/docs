# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Antora-based documentation site for the Package Distribution project. Documentation is written in AsciiDoc format and built into a static site.

## Common Commands

```bash
# Install dependencies
npm install

# Build the documentation site (outputs to public/)
npm run build

# Build and preview locally on http://localhost:8080
npm run preview
```

## Testing Locally

After running `npm run preview`, the site will be available at http://localhost:8080. You can also manually serve the `public/` directory after building with any static file server.

## Architecture

### Antora Configuration

- **antora-playbook.yml**: Main configuration defining site title, content sources, UI bundle, and output directory
- **docs/antora.yml**: Component descriptor defining component name, title, and version

### Content Organization

Documentation source files are in `docs/modules/ROOT/`:
- **nav.adoc**: Defines the navigation menu structure
- **pages/*.adoc**: Individual documentation pages in AsciiDoc format

### Adding New Pages

1. Create a `.adoc` file in `docs/modules/ROOT/pages/`
2. Add an entry to `docs/modules/ROOT/nav.adoc` to include it in navigation
3. Run `npm run build` or `npm run preview` to see changes

### Deployment

GitHub Actions automatically builds and deploys to GitHub Pages on pushes to `main`. The workflow uses `.github/workflows/deploy.yml` and publishes to the `gh-pages` branch.
