<!-- Guidance for AI coding agents working on this repo -->
# Repo overview

- This is a Jekyll-based academic website derived from the Minimal Mistakes theme. Key directories: `_layouts`, `_includes`, `_posts`, `_pages`, `_data`, `_sass`, `assets`, `markdown_generator`, and helper files like `talkmap.py` / `talkmap.ipynb`.
- The site is intended to be built with the `github-pages` gem (see `Gemfile`) and optionally uses npm scripts to build/minify JS (`package.json`).

# Big-picture architecture (what to know)

- Presentation: Liquid templates in `_layouts` and `_includes` compose pages. Common entrypoints:
  - `_layouts/default.html` — global HTML wrapper and layout inheritance
  - `_includes/masthead.html` — header / site masthead
  - `_includes/page__hero.html` — hero/banner blocks used across pages
- Content: Markdown posts and pages live under `_posts`, `_pages`, and `_talks`. Each content file uses YAML front matter for metadata (date, layout, author, categories, etc.).
- Data-driven pieces: `_data/*.yml` (for example `_data/authors.yml` and `_data/navigation.yml`) populate templates via `site.data`.
- Assets: CSS/Sass in `_sass/` and `assets/css/`. JS assets are built/minified to `assets/js/main.min.js` by npm scripts.

# Developer workflows (concrete commands)

- Install dependencies (root of repo):

  - Ruby + Bundler + Node required.
  - Install gems and node deps:

    - `bundle install`
    - If you encounter a GitHub Pages security warning, the README suggests removing `Gemfile.lock` and re-running `bundle install`.

- Serve locally (live reload):

  - Preferred (per README): `bundle exec jekyll liveserve`
  - If `liveserve` is unavailable, fallback: `bundle exec jekyll serve` (serves on http://localhost:4000).

- JS asset tasks (root):

  - Build minified JS: `npm run build:js` (runs `uglify` defined in `package.json`).
  - Watch JS changes and rebuild: `npm run watch:js`.

# Project-specific conventions and patterns

- Theme modifications: this repo is a customized Minimal Mistakes theme; many style/layout changes are in `_sass/` and `_includes/`. Avoid renaming theme files unless necessary because upstream merges are handled manually.
- Content metadata: add posts in `_posts/` with filenames `YYYY-MM-DD-title.md` and include YAML front matter. Use `author: <id>` that maps to `_data/authors.yml`.
- Static files: uploaded files should go into `files/` and are referenced from the site root (e.g., `/files/example.pdf`).

# Integration points & external dependencies

- GitHub Pages: `Gemfile` pins `github-pages` — build and tests should use `bundle exec` to ensure correct plugin versions.
- Node toolchain: `npm` scripts only handle JS minification; CSS/Sass is compiled by Jekyll (via `sass` in the Jekyll pipeline).
- Helper scripts: `markdown_generator/` and `talkmap.py` are local utilities used to generate markdown from TSV or other data sources. Treat them as standalone helpers — run with Python in a virtualenv when needed.

# How AI agents should modify code

- Minimal, targeted edits: prefer small, well-scoped changes (e.g., modify a single include or partial). When changing templates, update both the Liquid include (`_includes`) and any affected layout (`_layouts/default.html`).
- When changing authors/navigation, update `_data/*.yml` and search for usages via `site.data` or Liquid includes.
- JS changes: update `assets/js/_main.js` (or plugin files) and run `npm run build:js` to regenerate `assets/js/main.min.js`.

# Examples (use these as patterns)

- Add an author: edit `_data/authors.yml`, then reference the author id in a post's front matter `author: ryan`.
- Change header: edit `_includes/masthead.html` and verify visuals by running `bundle exec jekyll liveserve`.
- Update CSS variables: edit `_sass/_variables.scss`, then refresh the local site to see compiled changes.

# Notes, gotchas, and tips

- The README explicitly mentions removing `Gemfile.lock` if GitHub Pages reports a security vulnerability; follow that if `bundle install` fails.
- Windows: the Gemfile includes `wdm` for file watchers. Use `bundle exec` on Windows as well.
- Upstream merges: this is a forked/customized theme; expect merge conflicts when syncing with upstream theme changes. Keep theme-only changes grouped so they are easier to re-apply.

# If something is unclear

- Ask for the expected local commands to run (Windows vs WSL), or whether Python helpers should be containerized. If you want, I can run the build steps locally (if you permit) and capture the output.

-- End of guidance --
