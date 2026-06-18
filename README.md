# Koki Okumura Academic Website

This repository contains the source for Koki Okumura's academic website, built
with Quarto.

This README is the source of truth for the current site. The site is currently a
single-page website rendered from `index.qmd`.

## Current Structure

- `_quarto.yml` configures the Quarto website and currently renders only
  `index.qmd`.
- `index.qmd` contains the public homepage, research list, publication list, and
  links to local PDF files.
- `assets/` contains website styling and images.
- `files/` contains public files copied into the rendered site, including the CV
  and paper PDFs.
- `CV/` contains the source files for the CV. Its build output is not part of the
  published website.

## CV Workflow

The CV source is managed at `CV/Koki_CV.tex`.

```bash
cd CV
latexmk -pdf Koki_CV.tex
```

`CV/.latexmkrc` sends generated files to `CV/build/`. To update the public CV
used by the website, copy the built PDF to `files/Koki_CV.pdf` after reviewing
it.

## Local Preview

```bash
quarto render
quarto preview
```

Before publishing, also check the generated files:

```bash
find _site -maxdepth 3 -type f | sort
find _site/files -type f | sort
```

## Publishing Notes

- The `source` branch contains the Quarto source files.
- The `main` branch contains the rendered GitHub Pages output.
- To update the public site, edit the `source` branch, run `quarto render`,
  review `_site/`, then publish the contents of `_site/` to the `main` branch.
- Do not create `CNAME` until the GitHub Pages default URL has been checked.
- Do not switch DNS away from the current public site until the Quarto version
  has been reviewed on the GitHub Pages default URL.
- Public PDF links on the site should point to local `files/...` paths rather
  than Google Drive URLs.
- Keep public file paths stable after launch, especially CV and paper PDF URLs.
