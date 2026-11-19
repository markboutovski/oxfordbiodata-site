# oxfordbiodata.com

The Oxford BioData website: a single static HTML page, hosted on Netlify. There is no framework and no build step.

## What's in here

| File | What it is |
|---|---|
| `index.html` | The whole page: content, styles (in the `<style id="site">` block) and a small script at the bottom |
| `fonts/` | IBM Plex Sans and IBM Plex Mono, served from the site itself (no Google Fonts requests) |
| `favicon.svg` | Browser tab icon |
| `og-image.png` | 1200×630 image shown when the link is shared on LinkedIn, Slack, email, etc. |
| `netlify.toml` | Netlify settings: publish the repo root, cache the fonts |

## The page

One manifesto, read top to bottom:

1. A forest-green masthead carrying the company name.
2. One uninterrupted column of prose, opening with the thesis sentence (the `.lede` paragraph) and running through to the team paragraph. No headings, rules or diagrams interrupt it.
3. A slim forest-green band with the contact address.

## Editing

- **Text** lives directly in `index.html`, in page order: masthead, then the eight paragraphs of `<main>`, then the contact band. The paragraphs are plain `<p>` elements in reading order; add or remove them freely.
- **Colours and spacing** are defined once as CSS variables at the top of the `<style id="site">` block (`--forest`, `--green`, `--ink`, `--column` and so on). Change them there rather than in individual rules. `--column` sets the width of the reading column.
- **Contact email** appears in three places: the contact band near the bottom, the `mailto:` link on the same element, and the `application/ld+json` block in the `<head>`.
- **Page description and link preview text** are the `<meta name="description">` and `og:` tags in the `<head>`. If the positioning line changes, `og-image.png` needs regenerating too — it has the tagline baked into the picture.

British spelling throughout (`characterised`, `homogenising`), and `<html lang="en-GB">` to match.

To preview locally, run `python3 -m http.server` in this folder and open http://localhost:8000. Opening `index.html` straight from disk mostly works, but the fonts and the favicon are referenced from the site root (`/fonts/…`), so they only load when it is served.

## How changes go live

Netlify is linked to this repo:

- **Pull requests** get a free Deploy Preview link, posted on the PR by Netlify. Check your change there first.
- **Every commit to `main`** publishes to oxfordbiodata.com within about a minute.

The free Netlify plan allows about 20 publishes a month (each costs 15 of 300 monthly credits), so please group changes into one pull request and merge once, rather than committing small edits straight to `main`. When editing on github.com, choose "Create a new branch for this commit and start a pull request" in the commit dialog.
