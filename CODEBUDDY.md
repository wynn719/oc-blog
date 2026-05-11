# CODEBUDDY.md

This file provides guidance to CodeBuddy Code when working with code in this repository.

## Project Overview

A personal blog built with **Hugo** (extended edition required) using the **Blowfish** theme (v2.103.0). Content is in Chinese (`zh-CN`). Deployed to GitHub Pages at `https://kaorz.com/blog/`.

## Commands

```bash
# Local dev server (port 1313, live reload)
hugo server

# Build static site to public/
hugo

# Build with minification
hugo --minify

# Create new post (uses archetypes/default.md template)
hugo new posts/my-post.md
```

There are no test or lint commands in this project.

## Architecture

- **Static Site Generator**: Hugo. All pages are generated at build time — no SSR or SPA.
- **Theme**: Blowfish (`themes/Blowfish/`), installed as a git submodule. All layouts, partials, and shortcodes come from the theme. The project has **no custom layouts** in the root `layouts/` directory.
- **Styling**: Tailwind CSS v4 (handled by the theme). Color scheme is "slate" with light/dark mode toggle.
- **Search**: Client-side search via Fuse.js, enabled by JSON output format in `hugo.toml`.
- **Deployment**: GitHub Pages serving from the `docs/` directory on the master branch. After building, copy `public/` contents to `docs/` and commit to deploy.

## Directory Structure

```
hugo.toml                  # Main Hugo configuration (theme, params, markup, outputs)
config/_default/menus.toml # Navigation menus (overrides menu config in hugo.toml)
archetypes/default.md      # Template for new content
content/
  posts/                   # Newer blog posts
  archives/                # Legacy posts (2015-2016, migrated from Jekyll)
  archives.md              # Archives list page
  search.md                # Search page
docs/                      # GitHub Pages deployment target (pre-built site output)
public/                    # Hugo build output (gitignored)
resources/                 # Hugo resource cache (generated SCSS, etc.)
themes/Blowfish/           # Theme (gitignored, separate git repo)
layouts/                   # Empty — override theme layouts here if needed
```

## Key Configuration Details

- **hugo.toml** contains params, menu items, markup, and output settings. The `config/_default/menus.toml` file provides the actual menu configuration (more complete than the inline menu in hugo.toml).
- **go.mod** is stale — it still references `hugo-PaperMod` (the previous theme) rather than Blowfish. Hugo module resolution works because `themes/` is gitignored and the Blowfish theme is present as a local git clone.
- Content front matter uses `+++` delimiters (TOML format) for archetypes, but existing posts use `---` (YAML format). Both work in Hugo.
- The blog deploys under a subpath (`/blog/`), so all URLs are relative to that base.

## Content Management

All content is Markdown files in `content/`. Front matter fields: `title`, `date`, `draft`, `tags`, `categories`. Legacy posts in `archives/` have minimal front matter (many with empty tags/categories).

## Working with the Theme

- To override any theme template, create a matching file in the root `layouts/` directory (e.g., `layouts/partials/header.html` overrides `themes/Blowfish/layouts/partials/header.html`).
- Theme assets (CSS, JS) are in `themes/Blowfish/assets/` and processed by Hugo's asset pipeline.
- Do not modify files inside `themes/Blowfish/` directly — it is a separate git repository.
