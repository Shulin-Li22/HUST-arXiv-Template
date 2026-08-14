# Repository Guidelines

## Project Structure & Module Organization

This repository is a reusable LaTeX paper template. `paper.tex` is the main entry point: update metadata, abstract, resource links, figure paths, section order, and bibliography commands there. Editable paper content lives in `sections/`, with one `.tex` file per major section. `hust.cls` defines the document layout, typography, colors, headers, captions, and custom commands. Put bibliography entries in `main.bib`, source images in `pngs/`, and bundled fonts, logos, icons, and bibliography styles in `assets/`. Keep generated LaTeX intermediates out of commits; `.gitignore` already excludes them.

## Build, Test, and Development Commands

Build the PDF from the repository root:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error paper.tex
```

The output is `paper.pdf`. Run the command after changing `.tex`, `.bib`, class, or asset files; `latexmk` reruns the required LaTeX/BibTeX passes. There is no separate automated test suite or lint configuration. Treat a successful build and visual inspection of the resulting PDF as the validation step. The known `fancyhdr` `headheight` warning is non-blocking unless the rendered header is visibly incorrect.

## Coding Style & Naming Conventions

Use two spaces for continuation indentation, as in `paper.tex`, and keep one logical command or declaration per line where practical. Use descriptive, lowercase filenames for sections (for example, `modeltraining.tex`) and stable lowercase labels such as `fig:teaser`. Prefer existing macros and package conventions before adding new class-level behavior. Keep image paths relative to the repository root and preserve aspect ratio unless a deliberate crop or size change is required.

## Testing Guidelines

Before submitting changes, compile with the command above, confirm there are no fatal errors, and inspect page breaks, fonts, figures, hyperlinks, table of contents, references, and appendix formatting in `paper.pdf`. Replace all placeholder text and images before release.

## Commit & Pull Request Guidelines

This checkout contains no Git history or repository-specific contribution policy. Use short, imperative commit subjects such as `Update experiment section` or `Fix bibliography entry`, and keep unrelated formatting changes separate. Pull requests should describe the affected files and rendered-document impact, include the build command used, mention any remaining warnings, and attach before/after PDF screenshots when layout changes are involved.

## Configuration and Asset Safety

Do not commit personal credentials, private links, or large generated build artifacts. When replacing logos, fonts, or images, update all references in `paper.tex`, `sections/`, or `hust.cls` and verify that a clean checkout still compiles.
