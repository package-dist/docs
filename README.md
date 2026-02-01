# Package Distribution Documentation

This repository contains the documentation for the Package Distribution project, built using [Antora](https://antora.org/).

## Prerequisites

- [Node.js](https://nodejs.org/) (version 16 or higher)
- npm (comes with Node.js)

## Local Development

### 1. Install Dependencies

First, install the required dependencies:

```bash
npm install
```

This will install:
- `@antora/cli` - Antora command-line interface
- `@antora/site-generator` - Antora site generator

### 2. Build the Site

To build the documentation site:

```bash
npm run build
```

This command runs `antora antora-playbook.yml` and generates the static site in the `public/` directory.

### 3. Preview the Site

To build and preview the site locally:

```bash
npm run preview
```

This will:
1. Build the site using Antora
2. Start a local HTTP server on port 8080
3. Open your browser to `http://localhost:8080` to view the site

Alternatively, you can manually serve the `public/` directory after building:

```bash
# Build first
npm run build

# Then serve using any static file server
npx http-server public -p 8080
# or
python3 -m http.server 8080 --directory public
```

## Project Structure

```
.
├── docs/                          # Documentation source files
│   ├── antora.yml                # Component descriptor
│   └── modules/
│       └── ROOT/
│           ├── nav.adoc          # Navigation menu
│           └── pages/            # Documentation pages (AsciiDoc)
│               ├── index.adoc    # Landing page
│               └── what-is.adoc  # What is Package Distribution page
├── antora-playbook.yml           # Antora playbook configuration
├── package.json                  # Node.js dependencies and scripts
└── .github/workflows/deploy.yml  # GitHub Actions deployment workflow
```

## Writing Documentation

Documentation pages are written in [AsciiDoc](https://asciidoc.org/) format and stored in `docs/modules/ROOT/pages/`.

To add a new page:

1. Create a new `.adoc` file in `docs/modules/ROOT/pages/`
2. Add the page to the navigation in `docs/modules/ROOT/nav.adoc`
3. Build and preview to verify your changes

## Deployment

The site is automatically deployed to GitHub Pages when changes are pushed to the `main` branch. The GitHub Actions workflow (`.github/workflows/deploy.yml`) handles:

1. Installing dependencies
2. Building the site with Antora
3. Deploying to the `gh-pages` branch

The live site is available at: https://package-dist.github.io/docs

## Troubleshooting

### Build fails with UI bundle download error

If the build fails to download the UI bundle, check your internet connection. The build requires downloading the Antora UI bundle from GitLab.

### Changes not appearing

Make sure to rebuild the site after making changes to see them reflected in the preview.
