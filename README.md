# Personal CV — LaTeX source

This repository contains the LaTeX source for my personal Curriculum Vitae (CV) and an associated cover letter template.

## Overview

- Main CV source: `cv-on.tex`
- Styling and macros: `settings.sty`
- Rubrics/sections: `education.tex`, `employment.tex`, `projects.tex`, `skills.tex`, etc.
- Bibliography (optional): `own-bib.bib`
- Cover letter template and assets: `cover_letter/`

The repository is set up so you can compile the CV locally and customize the content and styling.

## Requirements

- TeX distribution (TeX Live or MacTeX)
- `latexmk` (recommended)
- `biber` (if you enable the bibliography)

On Debian/Ubuntu, install the basics with:

```bash
sudo apt update
sudo apt install -y texlive-latex-extra texlive-bibtex-extra texlive-fonts-recommended latexmk biber
```

On macOS, install MacTeX (or use Homebrew casks):

```bash
brew install --cask mactex
```

If you use fonts/packages that are missing, install the corresponding TeX packages or use `tlmgr` to add them.

## Build

Recommended (latexmk — handles runs, biber, cleanup):

```bash
cd /path/to/repo
latexmk -pdf cv-on.tex
```

If you need XeLaTeX (for CJK/Unicode fonts):

```bash
latexmk -xelatex cv-on.tex
```

Manual build (example):

```bash
pdflatex cv-on.tex
biber cv-on   # only if bibliography is enabled
pdflatex cv-on.tex
pdflatex cv-on.tex
```

Clean generated files:

```bash
latexmk -c
```

## Customization

- Edit your name and contact info in `cv-on.tex` (look for `\mynames{...}` and the header blocks).
- Tweak colors, margins and other styling in `settings.sty`.
- Add or remove rubrics by editing `\makerubric{...}` lines in `cv-on.tex` and the corresponding `.tex` sections.
- To enable the publication list, add `\addbibresource{own-bib.bib}` (already present but commented) and populate `own-bib.bib`.

## Git / Remote

A `.gitignore` is included and excludes common LaTeX build artifacts. If you want to track the generated PDF, remove `*.pdf` from `.gitignore`.

To create a GitHub repo and push (example using GitHub CLI):

```bash
gh repo create --public --source=. --remote=origin --push
```

Or manually:

```bash
git remote add origin git@github.com:USERNAME/REPO.git
git push -u origin main
```

## Troubleshooting

- Missing LaTeX packages: install the missing TeX packages via your package manager or `tlmgr`.
- Bibliography not showing: ensure you run `biber` (or let `latexmk` run it for you).

## License

This repository does not include a license by default. Add a `LICENSE` file if you want to set terms (e.g. MIT, CC-BY).

## Author / Contact

Edit the source files to update personal contact information. The template was adapted from an example CV template; keep or change attribution as you wish.
