# Docs Site Instructions
**TLDR:** The `docs/` directory is a plain static GitHub Pages site for VeriBench. Do not execute these files in the shell; list them with `find` or `ls`, preview them with `open` or a local HTTP server, and publish them by pointing GitHub Pages at `main / docs`.

## What this directory is

The `docs/` directory contains static site files for the VeriBench GitHub Pages site:

- `docs/index.html` is the site landing page.
- `docs/blog/veribench-launch/index.html` is the first blog-post draft.
- `docs/assets/site.css` is the shared stylesheet.
- `docs/.nojekyll` tells GitHub Pages to serve the site as plain static files.

## Common shell mistake

If you type a file path like `docs/.nojekyll` or `docs/index.html` directly into `zsh`, the shell tries to execute that file as a command.

That produces errors like:

```text
zsh: permission denied: docs/.nojekyll
```

This is expected. These files are content, not programs.

## Correct commands

List the files:

```bash
find docs -maxdepth 3 -type f | sort
```

Or inspect the directories:

```bash
ls -la docs docs/assets docs/blog/veribench-launch
```

## Preview locally on macOS

Open the pages directly in the browser:

```bash
open docs/index.html
open docs/blog/veribench-launch/index.html
```

Or run a local static server:

```bash
python -m http.server 8000 --directory docs
```

Then visit:

```text
http://localhost:8000
```

## Publish on GitHub Pages

In the GitHub repository settings:

1. Go to `Settings > Pages`.
2. Set `Source` to `Deploy from a branch`.
3. Select branch `main`.
4. Select folder `docs/`.

After that, GitHub Pages should serve this site from the repo's Pages URL.
