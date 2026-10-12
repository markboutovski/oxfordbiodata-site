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

## Editing

- **Text** lives directly in `index.html`, in page order: hero, the platform diagram, "Work with Oxford BioData", contact.
- **Colours and spacing** are defined once as CSS variables at the top of the `<style id="site">` block (`--forest`, `--green`, `--ink` and so on). Change them there rather than in individual rules.
- **Contact email** appears in two places: the contact section near the bottom of `index.html`, and the `application/ld+json` block in the `<head>`.
- **Page description and link preview text** are the `<meta name="description">` and `og:` tags in the `<head>`.

To preview locally, open `index.html` in a browser. Fonts load properly only when served from a web server, so for an exact preview run `python3 -m http.server` in this folder and open http://localhost:8000.

## How changes go live

Netlify is linked to this repo:

- **Pull requests** get a free Deploy Preview link, posted on the PR by Netlify. Check your change there first.
- **Every commit to `main`** publishes to oxfordbiodata.com within about a minute.

The free Netlify plan allows about 20 publishes a month (each costs 15 of 300 monthly credits), so please group changes into one pull request and merge once, rather than committing small edits straight to `main`. When editing on github.com, choose "Create a new branch for this commit and start a pull request" in the commit dialog.
