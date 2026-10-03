# F3 Dallas website: rules for AI assistants

This repo is the **pre-built static output** of the F3 Dallas site (built with vinext).
There is no source code, no package.json and no build step. Edit the files directly.
Every push to `main` deploys to https://f3dallas.com via Vercel.

## Changing text or content on a page

Page content exists in TWO places. Change BOTH, with the exact same text:

1. The page's HTML file in the repo root: `index.html`, `what-is-f3.html`, `workouts.html`,
   `photos.html`, `t-claps.html`, `connect.html`, `disclaimer.html`, `privacy.html`.
2. `_next/static/chunks/site-app-live.js`, the same strings inside the minified JavaScript.

If you change only the HTML, React replaces it with the old text from the JS right after
the page loads. Search both files for the exact original string and replace it in both.
Escape quotes correctly for each file (HTML entities in .html, JS string rules in .js).

## Images

Put new images in `images/f3-dallas/` and reference them as `/images/f3-dallas/<name>`
in both the HTML and `site-app-live.js`.

## Do not

- Do not rename `site-app-live.js` or edit any other file in `_next/static/`. Those files are
  cached by browsers for a year, so changes to them would not reach returning visitors.
- Do not remove the Vercel Analytics `<script>` tags in each page's `<head>`.
- Do not change `vercel.json` unless asked; it handles routing, caching and redirects.
- Do not add a build step, package.json or framework config.

## Before finishing

- Confirm every changed string was updated in both the HTML file and `site-app-live.js`.
- Keep changes minimal and describe exactly what text changed, on which page.
