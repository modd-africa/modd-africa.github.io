# MoDD Africa website

Quarto site for the MoDD Africa malaria-modelling network. Deploys to GitHub Pages via Actions on merge to `main`.

## Workflow (important)
- Team repo: never commit directly to `main`. Work on a branch → push → open a PR for review → merge.
- Do NOT commit the generated `_site/` folder.
- After edits, run `quarto preview` to check before committing.

## Structure
- English pages at repo root (`index.qmd`, `project.qmd`, `team.qmd`, `partners.qmd`, `news.qmd`).
- French twins in `fr/` — same filenames. Keep EN and FR in sync: any change to an English page must be mirrored in its `fr/` version.
- Images in `assets/`. French pages reference images as `../assets/...`; root pages as `assets/...`.
- All styling/design tokens live in `theme.scss` (green + forest + white palette; Sora/Inter fonts). Nav, banner and footer config in `_quarto.yml`.

## Conventions
- Home-page and card sections are written as raw HTML inside ```{=html}``` blocks — always close the fence.
- Keep content accurate: Nigeria hub is NIMR; malaria vector is Anopheles.