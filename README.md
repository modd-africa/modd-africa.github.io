# MoDD Africa — project website

Source for the **MoDD Africa** (Modelling for Decisions in a Dynamic Africa) public landing site, built with [Quarto](https://quarto.org). It's a static site: plain `.qmd` source renders to HTML and deploys to GitHub Pages via GitHub Actions.

## Structure

```
.
├── _quarto.yml              # site config: navbar, footer, theme, fonts
├── theme.scss               # design system (palette, type, components)
├── index.qmd                # home (hero + network graphic, in one HTML block)
├── project.qmd              # background, ERA approach, work packages
├── hubs.qmd                 # the three country hubs + partners
├── evidence-synthesis.qmd   # the Evidence Synthesis Unit + moddafricaes package
├── engage.qmd               # training, hackathons, community of practice
├── contact.qmd              # leadership + links
├── 404.qmd                  # not-found page
├── assets/brand.svg         # logo + favicon
└── .github/workflows/publish.yml   # CI: render + deploy to gh-pages
```

## Edit content

Most pages are ordinary Markdown — edit the prose directly in each `.qmd`. The home page (`index.qmd`) is a single raw-HTML block because of its custom hero layout and the inline network graphic; the comments mark each section.

Design tokens (colours, fonts, spacing, components) all live in `theme.scss`. Change a colour once there and it propagates across the site.

## Preview locally

1. Install Quarto: <https://quarto.org/docs/get-started/>
2. From this folder:

   ```bash
   quarto preview
   ```

   This serves the site at a local URL and live-reloads as you edit. To build once into `_site/`:

   ```bash
   quarto render
   ```

The fonts (Space Grotesk, IBM Plex Sans, IBM Plex Mono) load from Google Fonts, so a network connection is needed for them to appear correctly.

## Deploy to GitHub Pages

The included workflow (`.github/workflows/publish.yml`) renders the site and pushes the output to a `gh-pages` branch on every push to `main`.

**First-time setup**

1. Create the repository under the `modd-africa` organisation and push this folder to `main`.
2. The `Publish site` action runs automatically and creates the `gh-pages` branch.
3. In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, then choose **`gh-pages` / `(root)`** and save.
4. The site goes live a minute or two later.

No R or Python runtime is configured in CI because this site has no executed code cells. If you later add `{r}` or `{python}` cells, add the matching setup step to the workflow and turn on [freeze](https://quarto.org/docs/projects/code-execution.html#freeze).

## Where it will be served

This is configured for an **organisation site** repo named `modd-africa.github.io`, which serves at the clean root URL:

```
https://modd-africa.github.io
```

If you instead use a normal project repo (e.g. `modd-africa/website`), the site serves under a subpath:

```
https://modd-africa.github.io/website/
```

In that case, update `site-url` in `_quarto.yml` to match. Internal links use relative `.html` paths, so they work either way.

**Custom domain** (optional): set it under Settings → Pages, add a `CNAME` file with the domain, and update `site-url` in `_quarto.yml`.

## Notes

- Hub leads for DRC and Nigeria, partner organisations, and a project email address are marked as placeholders in the relevant pages — fill them in as they're confirmed.
- The `moddafricaes` usage on the Evidence Synthesis page mirrors the package README; keep it in sync if the package's API changes.
