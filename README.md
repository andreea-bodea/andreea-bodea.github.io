# Andreea Bodea — Academic Portfolio

Personal academic portfolio website built with [Hugo](https://gohugo.io/) and the [HugoBlox Academic CV](https://github.com/HugoBlox/hugo-theme-academic-cv) template. Showcases research publications, professional experience, education, and more.

## Tech Stack

- **Hugo** v0.156.0 (Extended) — static site generator
- **HugoBlox Academic CV** — modular Hugo theme
- **Tailwind CSS** v4 — styling
- **Pagefind** — static search indexing
- **pnpm** — package manager

## Development

```bash
# Install dependencies
pnpm install

# Start dev server
pnpm dev

# Production build (Hugo + Pagefind search index)
pnpm build
```

## Project Structure

```
content/             # Site content (Markdown)
  _index.md          # Homepage (block-based layout)
  authors/           # Author profile and metadata
  publications/      # Research publications (one folder per paper)
data/authors/me.yaml # Author profile, experience, education, skills
config/_default/     # Hugo & site configuration (YAML)
  params.yaml        # HugoBlox theme & site settings
layouts/partials/    # Custom layout overrides
static/uploads/      # PDFs (CV, papers, theses)
assets/media/        # Images and media
```

## Deployment

Deployed to **GitHub Pages** via GitHub Actions on push to `main`. The workflow runs `pnpm build` and publishes the `public/` directory.

## License

MIT © 2016-Present [George Cushen](https://georgecushen.com)
