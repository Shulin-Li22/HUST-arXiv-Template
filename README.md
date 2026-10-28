# HUST arXiv Template

An unofficial LaTeX template for arXiv papers and technical reports from Huazhong University of Science and Technology (HUST). The design uses HUST blue `#004B84`, HUST red `#D20B17`, and gray `#575757`.

## Quick Start

Compile from the repository root:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error paper.tex
```

The output is `paper.pdf`. Replace the placeholder title, authors, affiliations, abstract, links, figures, and section text before submission.

## Chinese Papers

Chinese papers use a separate entry point and section files so they remain independent from the English template:

```bash
latexmk -xelatex -interaction=nonstopmode -halt-on-error paper_zh.tex
```

Edit `paper_zh.tex`, the files in `sections/zh/`, and `main_zh.bib`. The Chinese entry point uses the Fandol fonts bundled with TeX Live through `xeCJK`; the existing `paper.tex`, `sections/`, and `main.bib` remain the English version and continue to use pdfLaTeX.

## Layouts

Single-column is the default:

```tex
\documentclass[]{hust}
```

Enable two-column body text with:

```tex
\documentclass[twocolumn]{hust}
```

In two-column mode, the title, authors, abstract, Paper Overview, and Contents remain full width. The two-column body starts at `Introduction`.

## Author Information

Edit the metadata near the top of `paper.tex`:

```tex
\author[1]{First Author}
\affiliation[1]{School of XXX, Huazhong University of Science and Technology}
\email{who1@hust.edu.cn}
\contribution{\textsuperscript{*} Equal Contribution}
\correspondence{who1@hust.edu.cn}
```

Affiliations are printed one per line. Add one `\email{...}` command for each author as needed.

## Logo and Assets

The default header uses `assets/hust-logo2.pdf`. To use the complete emblem, uncomment the logo overrides in `paper.tex`:

```tex
\renewcommand{\hustlogo}{assets/hust-logo1.pdf}
\renewcommand{\hustlogowidth}{24mm}
```

The template currently uses LaTeX-drawn placeholder boxes for paper figures, avoiding bundled sample photographs. Replace each `\templatefigure{...}` call in `paper.tex` or `sections/` with `\includegraphics` when adding your own licensed figures.

## Tables, Algorithms, and References

`booktabs` is used for three-line tables. `algorithm` and `algpseudocode` are available for pseudocode examples. References use numeric IEEE formatting:

```tex
\cite{sample_reference}
```

```tex
\bibliographystyle{IEEEtran}
\bibliography{main}
```

## Repository Structure

- `paper.tex`: document entry point and metadata.
- `hust.cls`: HUST theme, layout, typography, title block, and author metadata.
- `sections/`: editable paper sections and examples.
- `assets/`: fonts, logos, icons, and bibliography style resources.
- `main.bib`: BibTeX database.

## Copyright and License

Copyright (c) 2026 HUST arXiv Template contributors.

This is an unofficial community template and is not affiliated with, endorsed by, or sponsored by Huazhong University of Science and Technology. Before publishing this repository on GitHub, add a root-level `LICENSE` file specifying the open-source license for the template. Check the separate usage terms for bundled fonts, logos, and other third-party assets.

## Acknowledgments

Template reference: ByteDance Seed.

This template is adapted from [choucisan/arXiv-Template](https://github.com/choucisan/arXiv-Template), a clean arXiv-style LaTeX template with a polished title block and editable section structure.
