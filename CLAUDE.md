# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Rohin Siddhartha's personal portfolio/blog, deployed via GitHub Pages at `pvrohin/pvrohin.github.io`. It is a Jekyll site that uses the upstream [yousinix/portfolYOU](https://github.com/yousinix/portfolYOU) theme via `remote_theme` (unpinned) with the `github-pages` gem. Most of the repo is content, not code.

## Commands

```bash
bundle install
bundle exec jekyll serve      # local preview at http://localhost:4000 with rebuild on change
bundle exec jekyll build      # outputs to _site/
```

There are no tests or linters and no CI workflow; "does `jekyll build` succeed" is the check. `remote_theme` is fetched from GitHub at build time, so builds need network access.

## Architecture

The theme's layouts, most includes (`landing.html`, `blog/*`, `projects/*`, `about/skills.html`), and SCSS are **not in this repo**; they come from the remote theme. To change one, recreate it at the same path locally (override model). The only local override is `_includes/about/timeline.html`, which renders `experience` and `education` from `_data/timeline.yml` (a mapping with those two keys, latest first, `to: present` for current roles). This differs from the stock theme's flat list.

Content is split across:
- `pages/*` — each page's `weight` sets navbar order (Projects 1, Blog 2, About 3, Skills 4, Resume 5). `index.md` just includes the theme's `landing.html`; `404.html`, `tags.html`, `search.json` and `index.md` are excluded from the navbar via `nav_exclude` in `_config.yml`. `resume.md` embeds a PDF from `assets/Resume/` in an iframe.
- `_projects/` — a Jekyll collection (`output: true`, permalink `/projects/:name`, layout `page` via `defaults`). Front matter: `name`, `tools`, `image`, `description`. Bodies are Markdown/HTML with images from `assets/<ProjectName>/`.
- `_posts/` — blog posts, permalink `/blog/:title`, comments disabled by default.
- `_data/` — `timeline.yml`, `programming-skills.yml`, `other-skills.yml` (skill bars with `name`, `percentage`, `color`), `social-media.yml`.
- `assets/` — images are grouped in per-project/per-post folders (`AIC/`, `Rover/`, `post_1/`, ...), plus `Rohin.jpg` and the resume PDF.

`_config.yml` still contains placeholder values for unused social handles (`behance`, `facebook`, `medium`, `twitter` set to `your_username`), and Disqus/analytics/buymeacoffee are disabled. The `elements` collection and `documentation/**` nav exclude are leftovers marked "For Documentation Only" from the theme.

## Gotchas

- `_site/` (build output) is **tracked in git** and not in `.gitignore`, so every local build creates a large diff there. Avoid committing `_site/` changes unless intentional.
- `_config.yml` `exclude` lists `CLAUDE.md`, `README.md`, `CONTRIBUTING.md`, `LICENSE` and `projects_list_links.txt` (a scratch list of GitHub repo URLs, not used by the site). Any new non-site file at the root should be added there or it will be copied into `_site/`.
- `.claude/` is gitignored.
- Changes to `_config.yml` are not picked up by `jekyll serve` live reload; restart the server.
- Page/post/project asset paths are absolute from the site root (e.g. `/assets/AIC/AIC.png`), which works because `baseurl` is empty.
