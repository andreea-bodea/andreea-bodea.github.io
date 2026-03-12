# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an academic portfolio website built with **Hugo** (static site generator) and the **HugoBlox Academic CV** template. The site showcases research publications, professional experience, education, and personal information.

**Technology Stack:**
- Hugo v0.156.0 (Extended version required)
- HugoBlox framework (modular Hugo theme system)
- Tailwind CSS v4
- Pagefind (static search indexing)
- pnpm (package manager)

**Deployment:** GitHub Pages via GitHub Actions (can also deploy to Netlify)

## Development Commands

```bash
# Install dependencies
pnpm install

# Start development server (recommended)
pnpm dev
# Equivalent to: hugo server --disableFastRender

# Build for production
pnpm build
# Runs: hugo --minify && pnpm run pagefind

# Build search index only
pnpm run pagefind
```

## Architecture

### Content Organization

All site content lives in **Markdown** files:

- `content/_index.md` - Homepage with section blocks (biography, research, publications, experience, education, skills)
- `content/authors/_index.md` - Author profile metadata (the "me" user)
- `content/publications/` - Research publications (one folder per publication with `index.md`)
- `content/experience.md` - Professional experience timeline
- `static/uploads/` - PDF files (CV, papers, theses)
- `assets/media/` - Images and media assets

### Configuration Files

Configuration is split across multiple YAML files:

- `hugoblox.yaml` - HugoBlox-specific settings (theme, identity, SEO, analytics)
- `config/_default/hugo.yaml` - Hugo core configuration
- `config/_default/params.yaml` - Site parameters and HugoBlox settings (alternative to hugoblox.yaml)
- `config/_default/menus.yaml` - Navigation menu structure
- `config/_default/languages.yaml` - Internationalization settings
- `config/_default/module.yaml` - Hugo module imports (HugoBlox components)

**Key distinction:** This site uses `hugoblox.yaml` for HugoBlox configuration. Settings can alternatively be placed in `config/_default/params.yaml` under `hugoblox:` key.

### HugoBlox Block System

The homepage (`content/_index.md`) uses a **block-based layout** system. Each block is defined in the `sections:` array with:
- `block:` - Block type (e.g., `resume-biography-3`, `collection`, `markdown`, `resume-experience`)
- `content:` - Block-specific content and configuration
- `design:` - Visual styling and layout options

Example blocks used:
- `resume-biography-3` - Profile with avatar, bio, and education
- `markdown` - Custom markdown content sections
- `collection` - Display filtered content (e.g., publications)
- `resume-experience` - Work experience timeline
- `resume-education` - Education timeline
- `resume-skills` - Skills listing
- `resume-languages` - Language proficiency

### Module System

Hugo modules (Go modules) are used to import HugoBlox components:
- `github.com/HugoBlox/kit/modules/blox` - Core blocks and components
- `github.com/HugoBlox/kit/modules/slides` - Presentation slides support
- `github.com/HugoBlox/kit/modules/integrations/netlify` - Netlify deployment integration

Run `hugo mod get -u` to update modules.

### Custom Layouts

Optional layout overrides can be placed in `layouts/` directory following Hugo's lookup order. This site has minimal custom layouts in `layouts/partials/` for hook customizations.

## Common Tasks

### Adding a Publication

1. Create a new folder in `content/publications/` (e.g., `my-paper/`)
2. Add `index.md` with frontmatter:
```yaml
---
title: "Paper Title"
authors: ["me", "Co-Author"]
date: 2026-01-01
publication_types: ["article-journal"]  # or "paper-conference", etc.
publication: "*Journal Name*"
featured: true  # Show on homepage
links:
  - name: PDF
    url: uploads/paper.pdf
---
```
3. Add the PDF to `static/uploads/`
4. The publication will auto-appear on the homepage (if `featured: true`) and publications page

### Modifying the Homepage

Edit `content/_index.md`. Each section is a block - you can:
- Reorder blocks by moving them in the `sections:` array
- Add new blocks (see HugoBlox documentation for available block types)
- Customize block content and design parameters
- Hide blocks by removing or commenting them out

### Updating Profile Information

The primary author profile is in `content/authors/` (the folder is typically named `me` or `admin`). This contains:
- Profile metadata (name, bio, education, experience, skills)
- Avatar image
- Social links

Edit the `_index.md` file in the author folder to update personal information.

### Changing Site Branding

Edit `hugoblox.yaml`:
- `identity.name` - Site name (shown in navbar and footer)
- `identity.description` - SEO meta description
- `theme.mode` - Color mode (light/dark/system)
- `theme.pack` - Theme preset (default, minimal, ocean, etc.)
- `header.style` - Navigation style (navbar, navbar-simple, minimal)

### Enabling Search

Search is enabled by default via Pagefind. The search index is built during `pnpm build`. To toggle search visibility in the header, edit `hugoblox.yaml`:
```yaml
header:
  search: true  # or false
```

## Build Process

The site builds in two stages:

1. **Hugo Build** (`hugo --minify`)
   - Processes markdown content into HTML
   - Compiles Tailwind CSS
   - Optimizes images
   - Outputs to `public/` directory

2. **Pagefind Indexing** (`pnpm run pagefind`)
   - Scans `public/` directory
   - Generates search index
   - Creates search UI assets

## Deployment

### GitHub Pages (Current Setup)

GitHub Actions workflow (`.github/workflows/deploy.yml`):
1. Triggered on push to `main` branch
2. Runs build workflow (`.github/workflows/build.yml`)
3. Deploys `public/` to GitHub Pages

The workflow checks `hugoblox.yaml` for `deploy.host` setting. Current value: `github-pages`.

### Netlify (Alternative)

For Netlify deployment:
1. Set `deploy.host: netlify` in `hugoblox.yaml`
2. Netlify automatically uses `netlify.toml` configuration
3. Build command and environment variables are pre-configured

## Hugo-Specific Notes

- **Content Types**: Hugo automatically determines content type from directory structure
- **Taxonomies**: The site uses `authors`, `tags`, and `publication_types` taxonomies
- **URL Structure**: Controlled by Hugo's section structure and permalink settings
- **Shortcodes**: HugoBlox provides custom shortcodes for rich content (see documentation)
- **Page Bundles**: Publications use "leaf bundles" (folder with `index.md` and assets)

## Important Files to Avoid Modifying

- `go.mod` / `go.sum` - Hugo module dependencies (update via `hugo mod get -u`)
- `.hugo_build.lock` - Hugo build cache (auto-generated)
- `node_modules/` - npm dependencies
- `public/` - Build output (regenerated on each build)
- `resources/` - Hugo's processed assets cache

## Getting Help

- HugoBlox Documentation: https://docs.hugoblox.com/
- Hugo Documentation: https://gohugo.io/documentation/
- Template Repository: https://github.com/HugoBlox/hugo-theme-academic-cv
