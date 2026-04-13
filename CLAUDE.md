# portfolYOU — Claude Context File

## Project Overview

**portfolYOU** is a free, open-source Jekyll portfolio and blogging theme designed to work seamlessly with GitHub Pages. It provides a minimal, animated, and responsive design for developers and creatives who want to showcase their work online.

- **Repository:** [yousinix/portfolYOU](https://github.com/yousinix/portfolYOU)
- **License:** MIT
- **Current Version:** v2.3.0
- **Tech Stack:** Jekyll, Bootstrap 4, Liquid templating, SCSS, JavaScript

---

## Architecture & Directory Structure

After installation, the expected project layout is:

```
<your-username>.github.io/
├── _data/                  # YAML data files (skills, timeline, social media)
│   ├── programming-skills.yml
│   ├── other-skills.yml
│   ├── timeline.yml
│   └── social-media.yml
├── _posts/                 # Blog posts (YYYY-MM-DD-post-name.md)
├── _projects/              # Portfolio project files (.md or .html)
├── pages/                  # Site pages (auto-added to nav bar)
│   ├── about.md
│   └── projects.html
├── assets/
│   ├── favicon.ico
│   └── css/
│       └── style.scss      # Custom styles (override point)
├── _config.yml             # Main site configuration
├── .gitignore
└── Gemfile
```

> The source repo also contains a `docs/` directory (used for the theme's own documentation site) and `_includes/elements/` for reusable UI components. These are stripped out during user installation.

---

## Configuration (`_config.yml`)

The central config file drives most of the site's behavior. Key sections:

```yaml
remote_theme: yousinix/portfolYOU   # or pin a version: yousinix/portfolYOU@v2.3.0

title: Your Name
description: Your tagline

author:
  name: Your Name
  github: your_github_username
  twitter: your_twitter_handle
  # ... other social handles

external_new_tab: true   # Opens external_url links in a new tab
```

All social network handles listed under `author` are automatically rendered in the footer.

---

## Content Types

### Local Projects (`_projects/`)

File naming: `project-name.md` or `project-name.html`

Required front matter:
```yaml
---
name: Project Name
tools: [Ruby, Jekyll, Bootstrap]
image: /path/or/url/to/image.png
description: Short project description shown in card view.
---
```
- Supports all image orientations (landscape, portrait, square).
- Body written in Markdown or HTML.
- Supports `external_url` to link to an external resource instead of a detail page.

### Remote Projects (auto-imported from GitHub)

Add to the front matter of `pages/projects.html`:
```yaml
---
remote_projects:
  - repo-name-1
  - repo-name-2
---
```
Fetches `name`, `description`, and `topics` from the public GitHub repository automatically. The repo must be public and belong to the authenticated user.

### Blog Posts (`_posts/`)

File naming: `YYYY-MM-DD-post-name.md`

Front matter:
```yaml
---
title: Post Title
tags: [Tag1, Tag2]
style: fill          # or: border (optional)
color: primary       # primary | secondary | success | danger | warning | info | light | dark
description: Optional excerpt; defaults to first 25 words of body.
---
```
- Tags are searchable and archived automatically.
- Disqus comments are supported (configure Disqus shortname in `_config.yml`).

### Pages (`pages/`)

File naming: `page-name.html` or `page-name.md`

Front matter:
```yaml
---
layout: default
title: Page Title
permalink: /page-permalink/
weight: 3           # Controls order in navigation bar
nav_exclude: false  # Set true to hide from nav
---
```
Pages are added to the navigation bar automatically based on `weight`.

---

## Data Files

### Skills (`_data/programming-skills.yml`, `_data/other-skills.yml`)

```yaml
- name: Ruby
  percentage: 85
  color: danger       # optional; defaults to primary
```

Rendered as animated progress bars on the About page.

#### Adding a Custom Skills Category

1. Create `_data/category_name-skills.yml` with the above format.
2. In `pages/about.md`, inside the skills `<div class="row">`:
   ```liquid
   {% include about/skills.html title="Category Name Skills" source=site.data.category_name-skills %}
   ```

### Timeline (`_data/timeline.yml`)

```yaml
- title: Job Title or Degree
  from: 2020
  to: 2023
  description: Brief description of the role or event.
```

### Social Networks (`_data/social-media.yml`)

Built-in networks are preconfigured. To add a custom network:
```yaml
network_name:
  url:   https://www.network_name.com/
  icon:  fab fa-icon     # FontAwesome v5 icon class
  color: 1da1f2          # Hex color for hover state
```
Then add `network_name: your_username` under `author` in `_config.yml`.

---

## Customization

portfolYOU uses an **override-based customization model** — no forking required. To change any theme file, recreate it in your own project at the same relative path.

**Custom favicon:**
Place your `favicon.ico` at `assets/favicon.ico`.

**Custom styles:**
Create `assets/css/style.scss`:
```scss
---
---
/* Your custom CSS here */
@import "portfolYOU";
```

---

## Elements & Includes

The theme ships with reusable Liquid include snippets located in `_includes/elements/`. These cover:
- Figures / images
- Videos (YouTube embed wrappers)
- Styled lists
- Buttons
- And more

Use them in any Markdown or HTML content file via standard `{% include %}` syntax.

---

## Dependencies

| Library | Version |
|---|---|
| Bootstrap | v4.3.1 |
| FontAwesome | v5.6.3 |
| jQuery | v3.3.1 |
| Popper.js | v1.14.6 |
| Animate.css | v3.7.0 |
| wow.js | v1.1.2 |
| Simple Jekyll Search | v1.7.2 |
| GitHub Buttons | v2.2.9 |
| pygments-css | autumn |

All dependencies are loaded via CDN — no local bundling required.

---

## Development & Local Testing

```bash
# Install dependencies
bundle install

# Serve locally (with live reload)
bundle exec jekyll serve

# Build for production
bundle exec jekyll build
```

Requires Ruby and Bundler. The `Gemfile` already includes the `github-pages` gem for full compatibility.

---

## Common Patterns & Conventions

- **Image paths** in projects can be relative (`/assets/img/project.png`) or absolute URLs.
- **External links**: Add `external_url: https://example.com` to any project/post/page front matter to redirect instead of rendering a detail page.
- **Nav ordering** is controlled by the `weight` key in page front matter (lower = earlier).
- **Post styling** is opt-in — omitting `style` and `color` uses the default unstyled card.
- **Remote projects** require the GitHub repository to be public and owned by the `author.github` user in `_config.yml`.
- **Pinning theme version**: Use `remote_theme: yousinix/portfolYOU@vX.Y.Z` to avoid breaking changes from upstream updates.

---

## Key Files for AI Assistance

When helping with this project, these are the most commonly modified files:

| File | Purpose |
|---|---|
| `_config.yml` | Site identity, author info, feature flags |
| `pages/about.md` | About page content and skills layout |
| `pages/projects.html` | Projects listing; remote_projects front matter |
| `_data/timeline.yml` | Education / experience timeline |
| `_data/programming-skills.yml` | Skill bars |
| `_data/social-media.yml` | Social network definitions |
| `assets/css/style.scss` | Custom CSS overrides |
| `_posts/` | Blog post files |
| `_projects/` | Portfolio project files |